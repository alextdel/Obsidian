**up::** [[My Vault/ATLAS/MOCs/Moodle Admin MOC|Moodle Admin MOC]]
**index::** [[+Index for Personal]]
 

**tags::** 

# Server Backup Script (Moodle) Manual

**Created:**  06 September 2023 at  15:12 hours.

___
### Note:
The following was produced using GPT 3.5 after a concerted development process. The script itself can be found here [[Server Backup Script (BASH)]]

# Step-by-Step Manual for the Bash Script

## Overview

This Bash script automates the backup and storage of a Moodle website. It utilizes AWS S3 for storage and msmtp for email communication. The script follows these main steps:

1. **Setup and Configuration**
2. **Maintenance Mode**
3. **Backup Moodle Data and Database**
4. **Transfer Backups to AWS S3**
5. **Cleanup Old Backups**
6. **Email Notifications**
7. **Exit Maintenance Mode**

# Staging Bash Script Manual

This manual provides a detailed analysis of the provided Bash script, which is used for automating Moodle backup and storage using AWS S3 and msmtp. The script includes various functions and steps to perform backups, transfer them to AWS S3, manage Moodle's maintenance mode, and handle error scenarios. The script also includes essential prerequisites and configuration constants. Below is a step-by-step breakdown of the script:

---

## 1. Prerequisites

Before using the script, ensure that the following prerequisites are met:

1. Up to date AWS CLI: Make sure you have the AWS Command Line Interface installed and up to date.

2. Server instance connected to LightSail Bucket: Ensure your server instance is correctly connected to an AWS LightSail Bucket.

3. msmtp installation with a configured log file and config file (`/etc/msmtprc`): msmtp is required for sending email notifications.

4. SPF TXT record setup within domain DNS: Create a TXT record in your domain's DNS settings to specify authorized email servers.

5. DKMS record setup within domain DNS: Set up a DKMS (DomainKeys Identified Mail) record in your domain's DNS settings to prevent mail rejection or detection as spam.

## 2. Configuration

### 2.1. msmtp Configuration (`/etc/msmtprc`)

Here's an example configuration file for msmtp (`/etc/msmtprc`):

```plaintext
defaults
auth          on
tls           on
tls_starttls  on
tls_certcheck on
logfile       /var/log/msmtp/msmtp.log

account brevo
host          smtp-relay.brevo.com
port          587
from          name@from_domain.com.au
user          brevo_smtp_user@email.com.au
password      brevo_smtp_account_password

account default : brevo
```

### 2.2. msmtp Log File

Ensure that the msmtp log file (`/var/log/msmtp/msmtp.log`) exists and that the msmtp user has write permissions to the directory (e.g., `permission 755`, owner:group='msmtp:msmtp').

### 2.3. SPF TXT Record

Create a TXT record in your DNS with SPF information. Example TXT record:

```plaintext
Type: TXT
Name: @
Data: v=spf1 include:spf.brevo.com include:spf.protection.outlook.com mx ~all
```

### 2.4. DKMS Record

Set up a DKMS (DomainKeys Identified Mail) record within the DNS, following instructions provided by your DNS provider.

---

## 3. Notes

- No use of `sudo` within this script; it assumes correct permissions.
- Ensure the database user has 'SELECT' and 'LOCK TABLES' permissions on the `tdlk_moodle` database.
- Functions are used for logging and email communication.
- Test this script and ensure no errors or permission problems occur before scheduling it as a cron job.

### 3.1. Moodledata Directory Permissions

For Moodledata directory permissions, follow these steps:

- Change ownership: `sudo chown -R bitnami:daemon /home/bitnami/moodledata`
- Set directory permissions to 770: `sudo find /home/bitnami/moodledata -type d -exec chmod 770 {} \;`
- Set file permissions to 660: `sudo find /home/bitnami/moodledata -type f -exec chmod 660 {} \;`

---

## 4. Variables and Constants

This section defines variables and constants used throughout the script.

### Script Code:

```bash
DATE=$(date +%Y-%m-%d-%H-%M-%S)
FILENAME_PREFIX="stag_tdlk_mdl_bu"
success=true

# Configuration Constants
readonly USER="bitnami"
readonly WEB_DIR="/opt/bitnami/apache/htdocs"
readonly DATA_DIR="/home/bitnami/moodledata"
readonly DB_NAME="tdlk_moodle"
readonly DB_USER="tdlk_mdl-dbuser"
readonly DB_PASS="AAMWExjYvgb4LbAA"
readonly BACKUP_DIR="/home/bitnami/tdlk_mdl_backups"
readonly BUCKET_NAME="tdlk-data01-20230905"
readonly EMAIL="techsupport@tiddalik.com.au"

readonly LOG_FILE="${BACKUP_DIR}/${FILENAME_PREFIX}_$DATE.log"
readonly BU_TAR_FILE="${BACKUP_DIR}/${FILENAME_PREFIX}_$DATE.tar.gz"
readonly BU_SQL_FILE="${BACKUP_DIR}/${FILENAME_PREFIX}_$DATE.sql"
```

---

## 5. Functions

The script defines several functions for specific tasks.

### 5.1. `log_message(current_date, message)`

This function is used for logging messages. It takes two inputs: `current_date` (timestamp) and `message`, and appends the message to the log file.

### Script Code:

```bash
# Function to log messages - takes two inputs eg. date and message
log_message() {
    local current_date="$1"
    local message="$2"
    echo "[$current_date] $message" >> "$LOG_FILE" 2>&1
}
```

### 5.2. `handle_error(error_message)`

This function handles errors. It logs the error message, sends an email notification, and exits the script with an error code.

### Script Code:

```bash
# Function to handle errors
handle_error() {
    local error_message="$1"
    log_message "$(date +%Y-%m-%d-%H-%M-%S)" "Error: $error_message"
    echo -e "Subject: Moodle Backup Failed \n\n$error_message" | msmtp "$EMAIL"
    exit 1
}
```

### 5.3. `put_moodle_in_maintenance_mode()`

This function places Moodle into maintenance mode using Moodle's `maintenance.php` script.

### Script Code:

```bash
# Put Moodle in maintenance mode #
put_moodle_in_maintenance_mode () {
    log_message "$(date +%Y-%m-%d-%H-%M-%S)" "Placing Moodle into maintenance mode"
    php $WEB_DIR/admin/cli/maintenance.php --enable
}
```

### 5.4. `remove_maintenance_mode()`

This function returns Moodle out of maintenance mode using Moodle's `maintenance.php` script. It also sends a failure email if `success` is set to `false`.

### Script Code:

```bash
# Function to remove maintenance mode
remove_maintenance_mode() {
    log_message "$(date +%Y-%m-%d-%H-%M-%S)" "Returning Moodle out of maintenance mode"
    php $WEB_DIR/admin/cli/maintenance.php --disable
    # Send a failure email when maintenance mode is removed due to an error
    if [ "$success" = "false" ]; then
        log_message "Sending failure email after maintenance mode removal"
        echo -e "Subject: Moodle Backup Failed \n\nA failure has been detected during backup. Please check the log file for more information." | msmtp "$EMAIL"
    fi
}
```

---

## 6. Checking Prerequisites

This section checks if essential frameworks (msmtp and aws-cli) are installed and configured correctly. If not, it handles errors accordingly.

### Script Code:

```bash
#

 Check if msmtp is installed and /etc/msmtprc exists
if ! command -v msmtp >/dev/null 2>&1 || [ ! -f /etc/msmtprc ]; then
    handle_error "msmtp is not installed or /etc/msmtprc does not exist. Please install msmtp and configure /etc/msmtprc before running this script."
fi

# Check if AWS CLI is installed
if ! command -v aws >/dev/null 2>&1; then
     handle_error "AWS CLI is not installed. Please install AWS CLI before running this script."
fi
```

---

## 7. Creating Backup Directory and Log File

This section ensures that the backup directory (`$BACKUP_DIR`) and log file (`$LOG_FILE`) exist, have the correct permissions, and are owned by the correct user and group.

### Script Code:

```bash
# Check if $BACKUP_DIR exists, and create it if not
if [ ! -d "$BACKUP_DIR" ]; then
    mkdir -p "$BACKUP_DIR" || handle_error "Failed to create directory $BACKUP_DIR"
    chown "$USER":"$(id -gn)" "$BACKUP_DIR" || handle_error "Failed to set owner and group for $BACKUP_DIR"
    chmod 755 "$BACKUP_DIR" || handle_error "Failed to set permissions for $BACKUP_DIR"
fi

# Create the log file if it doesn't exist
if [ ! -f "$LOG_FILE" ]; then
    touch "$LOG_FILE" || handle_error "Failed to create log file $LOG_FILE"
    chown "$USER":"$(id -gn)" "$LOG_FILE" || handle_error "Failed to set owner and group for $LOG_FILE"
    chmod 644 "$LOG_FILE" || handle_error "Failed to set permissions for $LOG_FILE"
fi
```

---

## 8. Putting Moodle in Maintenance Mode

The script places Moodle in maintenance mode using the `put_moodle_in_maintenance_mode` function. This step is essential to prevent data inconsistency during backup.

### Script Code:

```bash
# Put Moodle in maintenance mode #
put_moodle_in_maintenance_mode
```

---

## 9. Creating Backups

This section creates backups of the Moodle web directory and data directory while excluding unnecessary directories. It also backs up the MySQL database.

### Script Code:

```bash
log_message "$DATE" "Backing up Moodle web directory, data directory, and SQL database"

if ! tar -czvf "$BU_TAR_FILE" \
    --exclude="$DATA_DIR/sessions" \
    --exclude="$DATA_DIR/cache" \
    --exclude="$DATA_DIR/localcache" \
    --exclude="$DATA_DIR/lock" \
    --exclude="$DATA_DIR/trashdir" \
    --exclude="$DATA_DIR/temp" \
    "$WEB_DIR" "$DATA_DIR"; then
    handle_error "Failed to create Moodle web directory and data directory backup."
    success=false
fi

# Backup MySQL database
if ! mysqldump -u "$DB_USER" -p"$DB_PASS" "$DB_NAME" > "$BU_SQL_FILE"; then
    handle_error "Failed to create MySQL database backup."
    success=false
fi
```

---

## 10. Moving Backups to LightSail Bucket

Backups are transferred to the AWS LightSail Bucket using the AWS CLI (`aws s3api`). The script checks the exit status of these commands to ensure successful transfer.

### Script Code:

```bash
log_message "$DATE" "Moving backup to LightSail Bucket"

# Checks the exit status of aws s3api commands
if aws s3api put-object --bucket "$BUCKET_NAME" --key "${FILENAME_PREFIX}_$DATE.tar.gz" --body "$BU_TAR_FILE" --acl bucket-owner-full-control; then
    log_message "$DATE" "Backup tar.gz successfully moved to LightSail Bucket storage."
else
    handle_error "Error: Failed to move tar.gz backup to LightSail Bucket storage."
fi

if aws s3api put-object --bucket "$BUCKET_NAME" --key "${FILENAME_PREFIX}_$DATE.sql" --body "$BU_SQL_FILE" --acl bucket-owner-full-control; then
    log_message "$DATE" "SQL backup successfully moved to LightSail Bucket storage."
else
    handle_error "Error: Failed to move SQL backup to LightSail Bucket storage."
fi

# Log the success of the S3 storage
log_message "$DATE" "Backup successfully moved to LightSail Bucket storage."
```

---

## 11. Deleting Old Backups and Log Files

Backups and log files older than 7 days on the server are deleted. The script checks the exit status of the `find` and `rm` commands to ensure successful deletion.

### Script Code:

```bash
log_message "$DATE" "Deleting backups older than 7 days on the server"

# Check the exit status of find and rm commands
# Delete backups older than 7 days in the backup directory
if find "$BACKUP_DIR" -type f -name "*.tar.gz" -mtime +7 -exec rm -f {} \; ; then
    log_message "$DATE" "Tar.gz backups older than 7 days have been deleted on the server."
else
    handle_error "Error: Failed to delete tar.gz backups older than 7 days on the server."
fi

if find "$BACKUP_DIR" -type f -name "*.sql" -mtime +7 -exec rm -f {} \; ; then
    log_message "$DATE" "SQL backups older than 7 days have been deleted on the server."
else
    handle_error "Error: Failed to delete SQL backups older than 7 days on the server."
fi

# Delete log files older than 7 days
if find "$BACKUP_DIR" -type f -name "*.log" -mtime +7 -exec rm -f {} \; ; then
    log_message "$DATE" "Log files older than 7 days have been deleted on the server."
else
    handle_error "Error: Failed to delete log files older than 7 days on the server."
fi
```

---

## 12. Taking Moodle Out of Maintenance Mode

After completing the backup and cleanup tasks, the script returns Moodle out of maintenance mode using the `remove_maintenance_mode` function.

### Script Code:

```bash
# Take Moodle out of maintenance mode
remove_maintenance_mode
```

---

## 13. Logging Completion and Uploading Log File

The script logs the completion of the backup process and uploads the log file to the LightSail Bucket.

### Script Code:

```bash
log_message "$DATE" "Moodle backup completed on $DATE"

# Upload the log file to LightSail Bucket
if ! aws s3api put-object --bucket "$BUCKET_NAME" --key "${FILENAME_PREFIX}_$DATE.log" --body "$LOG_FILE" --acl bucket-owner-full-control; then
    handle_error "Error: Failed to upload log file to LightSail Bucket."
fi
```

---

## 14. Sending Email Notifications

Depending on the success of the backup process (`$success`), the script sends either a success or failure email notification to the specified email address (`$EMAIL`).

### Script Code:

```bash
# Send success/failure email
if $success; then


    echo -e "Subject: Moodle Backup Success \n\nMoodle backup completed successfully." | msmtp "$EMAIL"
else
    echo -e "Subject: Moodle Backup Failed \n\nA failure has been detected. Please check the log file for more information." | msmtp "$EMAIL"
fi
```

---

This manual provides a detailed understanding of the script, its functions, and each section's purpose. Before using this script, ensure all prerequisites are met, and the configuration constants are correctly set. Additionally, test the script thoroughly to avoid errors and issues during scheduled executions.


**See also::** [[Linux logger command]]

### Links to this note:
```query
"[[Moodle Backup Script Manual]]"
```

