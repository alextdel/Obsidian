**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #MySQL #MariaDB #database #migration 

# MySQL DB to Maria Migration

**Created:**  04 May 2023 at  09:57 hours.

___
### Note:
When attempting to migrate from a Lightsail DB to a LAMP database there are two errors caused by the versions of the DB (MySQL)  and that of the LAMP server (Maria)

---
1. Error when importing MySQL data dump file with the extension 'sql' into MariaDB 
   *"ERROR 1273 (HY000) at line 1: Unknown collation: 'utf8mb4_0900_ai_ci"*
   This error message indicates that the character set or collation specified in the SQL dump file is not supported by MariaDB. The collation 'utf8mb4_0900_ai_ci' is a new collation introduced in MySQL version 8.0, which may not be supported by the MariaDB version. 
   
   These steps rectified this situation:

	1.  Open the SQL dump file using a text editor.
	2.  Search for the string "utf8mb4_0900_ai_ci" in the file.
	3.  Replace all occurrences of "utf8mb4_0900_ai_ci" with "utf8mb4_general_ci" or any other collation that is supported by your MariaDB version.
	4.  Save the modified SQL dump file.

	 The search and replace process can be done using the 'sed' command
	`sed -i 's/utf8mb4_0900_ai_ci/utf8mb4_general_ci/g' dumpfile.sql`

	This will will replace all occurrences of "*utf8mb4_0900_ai_ci*" with "*utf8mb4_general_ci*" in the "dumpfile.sql" file.

After making the necessary changes to the SQL dump file, try importing it again into MariaDB using the "mysql" command:

`mysql -u username -p database_name < dumpfile.sql`

Replace "username" with your MariaDB username, "database_name" with the name of the database you want to restore, and "dumpfile.sql" with the name of the modified SQL dump file.

--------------
***The above steps worked but the import failed again as there was another error***

---
2. Following the steps above this error message now appears 
   *ERROR 1193 (HY000) at line 26: Unknown system variable 'GTID_PURGED'*
   
   The "GTID_PURGED" system variable is used for Global Transaction ID (GTID) based replication, which allows for easy tracking and management of transactions across different servers. The MySQL dump file was likely created using GTID-based replication, however the MariaDB does not support GTID.

	To rectify this situation, you can try the following steps:
	
	1.  Open the SQL dump file using a text editor.
	2.  Search for the string "GTID_PURGED" in the file.
	3.  If you find any instances of "GTID_PURGED", remove them along with their associated values from the SQL dump file. Make sure not to delete any other important data from the file.
	   The line may look  something like - 
	   *SET @@GLOBAL.GTID_PURGED=/\*!80000 '+'\*/ '';*

	4.  Save the modified SQL dump file.

![[How to Import a MySQL Dump File#2. Import the .sql dump file:]]

---
3. Additional step that may be required

If the above solution does not work, it is possible that the MariaDB installation does support GTID, but the option has not been enabled. 
Enable GTID-based replication by adding the following line to your MariaDB configuration file (usually located at /etc/my.cnf or /etc/mysql/my.cnf):

`gtid_mode=ON`

After making the necessary changes to the configuration file, restart the MariaDB service and try importing the SQL dump file again.


---

**Note:** If you still encounter issues, it is possible that there are other compatibility issues between the MySQL dump file and the version of MariaDB you are using. In that case, you may need to consider alternative options such as exporting the data from MySQL in a different format, or upgrading your MariaDB installation to a version that supports the features used in the MySQL dump file.

---

**See also::** [[How to Import a MySQL Dump File]],  

### Links to this note:
```query
"[[MySQL DB to Maria Migration]]"
```


