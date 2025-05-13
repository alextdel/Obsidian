**up::** [[My Vault/ATLAS/MOCs/Linux MOC|Linux MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #log #logger #Linux #commands

# Linux logger command

**Created:**  20 July 2023 at  13:53 hours.

___
### Note:
The `logger -t` command is used to log messages to the system log. 
The `-t` option specifies a tag that is used to identify the messages. In this case, the tag is `moodle_backup`. This means that all of the messages that are logged with the `logger -t moodle_backup` command will be grouped together in the system log.

The `logger` command can be used to log messages to a variety of different destinations, including the system log, a file, or an email address. The destination that is used is determined by the options that are passed to the command.

In this case, the `logger` command is being used to log messages to the system log. The system log is a file that records all of the events that happen on a Linux system. This includes things like system startup, user logins, and application errors.

The `logger -t` command is a useful way to log the progress of a backup process. This can be helpful for troubleshooting if the backup process fails.

Here is an example of how the `logger -t` command can be used to log the progress of a backup process:

```
logger -t "moodle_backup" "Starting Moodle backup"
logger -t "moodle_backup" "Backing up Moodle web directory"
logger -t "moodle_backup" "Backing up Moodle data directory"
logger -t "moodle_backup" "Backing up Moodle SQL database"
logger -t "moodle_backup" "Moodle backup completed successfully"
```

This example shows how the `logger -t` command can be used to log the progress of a Moodle backup process. The messages that are logged will be grouped together in the system log under the tag `moodle_backup`. This will make it easy to find the messages if the backup process fails.


**See also::** [[Moodle Backup Script 2]], [[Moodle Backup Script 1]]

### Links to this note:
```query
"[[Linux logger command]]"
```

