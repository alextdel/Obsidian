**up::** [[Azure - Davros]]
**index::** [[+Index for Personal]]

**tags::** #staging #learn #moodle #davros #azure
# Mariadb for tiddalik.com.au

**Created:**  20 May 2024 at  17:25 hours.
___
### Set up and other notes
1. MariaDB is installed on the host Ubuntu server
2. Each Webmin domain has a database
	1. *tiddalik.com.au* domain has a mariadb called *tiddalikadmin*
		- user: *tiddalikadmin*
		- passwd: *rZ6SigJfdaov339*
	- Logging in to tiddalikadmin and running `Mariadb> show databases;` gives

	  ```sql
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| learn              |
| staging            |
| tiddalikadmin      |
+--------------------+
4 rows in set (0.001 sec)
```

This shows that: 
- *learn.tiddalik.com.au* domain is a sub domain of tiddalik.com.au and has a mariadb called *learn*
- *staging.learn.tiddalik.com.au* domain is a sub domain of tiddalik.com.au and has a mariadb called *staging* 


**See also::** 

### Links to this note:
```query
"[[staging.learn.tiddalik.com.au]]"
```

