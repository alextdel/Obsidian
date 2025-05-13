**up::** {enter link to appropriate MOC}
**index::** [[+Index for Personal]]
 

**tags::** 

# mysqldump with remote databases

**Created:**  12 May 2023 at  09:23 hours.

___
### Note:

For Moodle, the best practice is to put the server into maintenance mode [see here](obsidian://open?vault=My%20Vault&file=SPACES%2FMOODLE%2FMoodle%20Maintenance%20Mode)
1. A standard use of mysql dump - run from same machine as the database is stored:
```
sudo mysqldump -u [user] -p [database_name] > [filename].sql
```

2. This is to backup  an entire Database Management system by including all databases within the system including the system tables:
```
mysqldump --all-databases --single-transaction --quick --lock-tables=false > full-backup-$(date +%F).sql -u root -p
```

3. If the database is on a remote host ( a remote server )
```
mysqldump --all-databases --single-transaction --quick --lock-tables=false -h <remote_host> -u <username> -p > full-backup-$(date +%F).sql
```

4. To backup a single database on a remote host.
```
mysqldump -h <remote_host> -u <username> -p <database_name> > database-backup-$(date +%F).sql
```

Notes
-  *--quick* is not as crucial on a single database backup unless the tables are large - this setting assists when large tables are challenging the size of memory
- *--lock-tables=false* By default mysqldump locks tables to ensure data consistency. *false* can be set if  the tables are small and db usage is not likely to cause significant write operations which may cause data inconsistencies
- In the case of moodle, placing the system in maintenance mode prevents data interactions with the database and so locking is irrelevant..


**See also::** [[SPACES/LINUX & MOODLE TECH/Moodle Maintenance Mode]], [[How to Import a MySQL Dump File]], [[MySQL DB to Maria Migration]]


### Links to this note:
```query
"[[mysqldump with remote databases]]"
```

