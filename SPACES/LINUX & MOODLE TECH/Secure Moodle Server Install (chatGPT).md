**up::** [[Linux & Moodle MOC|Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #moodle #ChatGPT #AWS #installation

# Secure Moodle Server Install (chatGPT)

**Created:**  15 August 2023 at  18:35 hours.

___
### Note:
The following is an installation process provided by Chat GPT 3.5 (current knowledge as of Sept 2021).

In this plan, we use Ubuntu as the Linux distribution, Apache as the web server, MySQL as the database, and PHP for server-side scripting. We'll also set up scripted backups to an AWS S3 bucket and configure email communication for Moodle. Also includes firewall configuration, Git-based installation, backup setup, etc.

### Step 1: Set up an AWS Lightsail Instance

1. Log in to your AWS account.
2. Go to the Lightsail console.
3. Click "Create instance".
4. Choose a Linux/Unix platform (Ubuntu is recommended).
5. Select a plan according to your requirements.
6. Choose a hostname for your instance.
7. Click "Create instance".

### Step 2: Connect to Your Lightsail Instance

1. Obtain the SSH key from Lightsail or use your own SSH key.
2. Use your terminal to connect to the instance:
   ```bash
   ssh -i /path/to/your/key.pem ubuntu@your-instance-ip
   ```

### Step 3: Install Required Packages

1. Update package list and install necessary packages:
   ```bash
   sudo apt update
   sudo apt install apache2 mysql-server php php-mysql php-gd php-curl php-zip php-xmlrpc php-intl php-soap php-xml libapache2-mod-php unzip git ufw awscli ssmtp mailutils
   ```

### Step 4: Configure Firewall (UFW)

1. Configure firewall rules:
   ```bash
   sudo ufw allow OpenSSH
   sudo ufw allow 80/tcp      # Allow HTTP
   sudo ufw allow 443/tcp     # Allow HTTPS
   sudo ufw enable
   ```

### Step 5: Download and Install Moodle via Git

1. Clone the Moodle repository from GitHub:
   ```bash
   cd /var/www/html
   sudo git clone -b MOODLE_XYZ_STABLE https://github.com/moodle/moodle.git
   sudo mv moodle moodlecode
   ```

2. Set appropriate permissions:
   ```bash
   sudo chown -R www-data:www-data /var/www/html/moodlecode
   sudo chmod -R 755 /var/www/html/moodlecode
   ```

### Step 6: Configure Moodle

1. Open your browser and navigate to your server's IP address to start Moodle installation.
2. Follow the Moodle installation steps. Provide database and site information as required.
3. Configure ghost

### Step 7: Configure AWS CLI for Backup including moodledata and database backup.

#### Configure the AWS Command Line Interface (CLI) with the AWS credentials to ensure secure connections to the S3 bucket. 

1. If required ... Install AWS CLI (**should already be installed above**):
   ```bash
   sudo apt install awscli
   ```

2. Configure AWS CLI with your credentials:
   ```bash
   aws configure
   ```
Follow the prompts to enter the AWS Access Key ID, Secret Access Key, default region, and output format. This information can be obtained from your AWS account. Make sure you use proper IAM user credentials with the necessary permissions to access your S3 bucket.
#### Now create the backup script

3. Create a script to automate backups and upload to S3. For example, create a Bash script named `backup.sh`:
   ```bash
   #!/bin/bash
   timestamp=$(date +%Y%m%d%H%M%S)
   mysqldump -u your-db-username -p'your-db-password' your-db-name > /var/www/html/moodledata/backups/dbbackup_$timestamp.sql
   tar -zcvf /var/www/html/moodledata/backups/moodledata_backup_$timestamp.tar.gz /var/www/html/moodledata
   aws s3 cp /var/www/html/moodledata/backups/dbbackup_$timestamp.sql s3://your-s3-bucket/
   aws s3 cp /var/www/html/moodledata/backups/moodledata_backup_$timestamp.tar.gz s3://your-s3-bucket/
   ```
I have written a backup script called [[Server Backup Script (BASH)]] which is copied here and has a manual page called [[Server Backup Script (Moodle) Manual]]

4. Make the script executable:
   ```bash
   chmod +x backup.sh
   ```

#### Set up a cron job to run the script

3. Set up a cron job to run the backup script regularly:
   ```bash
   crontab -e
   # Add a line like the following to run the backup every day at 2 AM:
   # 0 2 * * * /path/to/backup.sh
   ```

### Step 8: Configure Email Communication
This uses MSMTP which is a 'send only' MTA for emails - ideally suited for script notifications from apps, for example the scripts here.
**Note** The firewall must be able to pass through traffic to port 587

1. Configure MSMTP (replaces the unsupported older SSMTP) by editing `/etc/msmtprc` 
2. Edit the `msmtprcf` configuration file:
   ```bash
sudo nano /etc/msmtprc
```
3. Configure the `msmtprc` file with the following parameters, adjusting them to match your email service provider's settings (in this case, AWS SES):
```shell
# Minimal configuration for msmtp
defaults
auth          on
tls           on
tls_starttls  on
tls_certcheck on

account brevo
# was SendinBlue
host          smtp-relay.brevo.com
port          587
from          ##[the from address for emails] eg. ##learn@tiddalik.com.au
user          ##[brevo account user] eg. ##admin01@tiddalikservices.com.au
password      ##[password from brevo smtp account]##

account default : brevo
```

Replace *your-email@example.com*, *your-smtp-username*, and *your-smtp-password'* with your AWS SES SMTP credentials.
    
4. Save and exit the editor.

5. Test sending an email:
   ```bash
   #To send from the command line to 123.adelaforce@gmail.com
   echo -e "Subject: this is the subject\n\nThis is the body" | msmtp 123.adelaforce@gmail.com
   #To send from the command line using the contents of a file
   echo -e "Subject: Your Subject Here\n" | cat - filename | msmtp recipient@example.com
   ```

### Step 9: Secure Your Installation

1. Install Let's Encrypt and configure SSL as described earlier.

### Step 10: Finalize and Test

Access your Moodle site using HTTPS and ensure everything works correctly.

Remember that this guide is meant to provide a general framework, and you should adjust it according to your specific requirements and any changes that have occurred since my last update. Always refer to the latest documentation and best practices to ensure a secure and up-to-date installation.

**See also::** [[Server Backup Script (BASH)]] [[Server Backup Script (Moodle) Manual]]

### Links to this note:
```query
"[[Secure Moodle Server Install (chatGPT)]]"
```

