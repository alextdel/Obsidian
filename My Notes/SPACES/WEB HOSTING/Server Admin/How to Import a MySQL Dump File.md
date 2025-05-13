**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #MySQL #MariaDB #migration #dump_file

# How to Import a MySQL Dump File

**Created:**  04 May 2023 at  10:33 hours.

___
### Importing a mysqldump file

#### 1. Prepare the database for the import
1. Make a new database in the mysql or maria system
```sql
CREATE DATABASE <database_name>
```
3. Set the privileges
```sql
GRANT ALL PRIVILEGES ON <destination_database>.* TO '<username>'@'<host>' IDENTIFIED BY '<password>';
```

***Note:*** 
If the destination database already exists and contains data that you want to remove before importing, you can *truncate* or *drop* the existing tables. Be cautious when performing these actions as they permanently remove data.
Start the mysql or maria prompt, then either:

- truncate all tables in the database:
```sql
TRUNCATE TABLE <table_name>;
```
or

- drop the entire database 
```sql
DROP DATABASE IF EXISTS <destination_database>;
```

Then make a fresh database (step 1 above) using the required database, then do step 2 above:

#### 2. Import the .sql dump file:
After making the necessary changes to the SQL dump file, importing it into MariaDB using the "mysql" command:

```bash
mysql -u <username> -p database_name < dumpfile.sql
```

Replace "username" with your MySQL/MariaDB username, "database_name" with the name of the database you want to restore, and "dumpfile.sql" with the name of the modified SQL dump file.


**See also::** [[mysqldump with remote databases]], [[MySQL DB to Maria Migration]]

### Links to this note:
```query
"[[How to Import a MySQL Dump File]]"
```

