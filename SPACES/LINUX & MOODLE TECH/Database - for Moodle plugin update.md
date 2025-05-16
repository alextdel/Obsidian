**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Moodle #database #barracuda #innodb_file_format #MariaDB #MySQL #Lightsail 

# Database - for Moodle plugin update

**Created:**  23 December 2022 at  18:46 hours.

___
### Note:

With the Bitnami LAMP instance and a seperate Lightsail DB for Moodle I got and error when trying to upgrade a plugin ... gives me this warning

![[Moodle other update checks.png]]
I have tried updating the file format to barracuda but can't do this on AWS Lightsail. This was an error due to different database in Lightsale DB than Moodle thinks.

The problem is that the Bitnami LMS image uses MariaDB **BUT** the Lightsail database is MySQL. This causes all sorts of issues if you don't realise (I didn't) as the innodb_file_type and several other parameters look incorrect but in fact the version of MySQL that the Lightsail DB uses has deprecated the settings that the online guides are refering to. The MySQL database is in fact absolutely fine but Moodle thinks the DB is a MariaDB.
1. Change the dbtype setting in the ***config.php*** file. 
	- open the config.php file (in Bitnami image this is in */opt/bitnami/apache2/htdocs* )
change
```
$CFG->dbtype    = 'mariadb'; 
```
to 
```
$CFG->dbtype    = 'mysqli';
```

2. Restart the services or reboot
3. Now edit the php.ini file to increase the 
4. max_input_vars to 5000
	- See https://docs.moodle.org/401/en/Environment_-_max_input_vars
5. Restart services and then reload the Moodle admin page and the database should now be set up correctly.






**See also::** 

### Links to this note:
```query
"[[Moodle Database - for plugin update]]"
```

