**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #cron #crontab #Moodle 

# Cron Job for Moodle

**Created:**  26 September 2022 at  17:50 hours.

___
### Note:
The cron job runs every minute and is this line in the bitnami cron file.

```
* * * * * sudo /opt/bitnami/php/bin/php /home/bitnami/htdocs/admin/cli/cron.php
```

To edit bitnami user's cron job::
```
> sudo crontab -e bitnami
```

To list a users cron job::
```
> sudo crontab -u username -l
```

**See also::** 

### Links to this note:
```query
"[[Cron Job for Moodle]]"
```

