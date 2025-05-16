**up::** [[TIDDALIK Web MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #moodle #password #username #database

# config.php file for learn Moodle

**Created:**  26 September 2022 at  10:41 hours.

___
### Note:
## Old Version from VentraIP :
### database for Tiddalik Learn:
Contents of config.php file
```
<?php  // Moodle configuration file

unset($CFG);
global $CFG;
$CFG = new stdClass();

$CFG->dbtype = 'mariadb';
$CFG->dblibrary = 'native';
$CFG->dbhost    = 'localhost';
$CFG->dbname    = 'tiddalik_mood602';
$CFG->dbuser    = 'tiddalik_mood602';
$CFG->dbpass    = '3()45yt!3MpGt@S.';
$CFG->prefix    = 'tdlmdltbl_';
$CFG->dboptions = array (
  'dbpersist' => 0,
  'dbport' => '',
  'dbsocket' => '',
  'dbcollation' => 'utf8mb4_general_ci',
);

$CFG->wwwroot   = 'https://learn.tiddalik.com.au';
$CFG->dataroot  = '/home/tiddalik/tdl_moodledata';
$CFG->admin     = 'admin';

$CFG->directorypermissions = 0777;

require_once(__DIR__ . '/lib/setup.php');

// There is no php closing tag in this file,
// it is intentional because it prevents trailing whitespace problems!
```

## New Version from AWS
### database for Tiddalik Learn: 
Data service on Lightsail
**username::** dbMDL_TDLKAdmin
**password::** doo##sf5uVwZLV
**endpoint::** ls-6a8fd009d6d429105a71740f4570200037693e0f.cbzwa8u8nscp.ap-southeast-2.rds.amazonaws.com
**port::** 3306

Moodle database restored into **AWS database name::** tdlk_learn01

This is the new ***config.php***
Stored in /home/bitnami/htdocs
```
<?php  // Moodle configuration file

unset($CFG);
global $CFG;
$CFG = new stdClass();

$CFG->dbtype = 'mariadb';
$CFG->dblibrary = 'native';
$CFG->dbhost    = 'ls-6a8fd009d6d429105a71740f4570200037693e0f.cbzwa8u8nscp.ap-southeast-2.rds.amazonaws.com';
$CFG->dbname    = 'tdlk_learn01';
$CFG->dbuser    = 'dbMDL_TDLKAdmin';
$CFG->dbpass    = 'doo##sf5uVwZLV';
$CFG->prefix    = 'tdlmdltbl_';
$CFG->dboptions = array (
  'dbpersist' => 0,
  'dbport' => '',
  'dbsocket' => '',
  'dbcollation' => 'utf8mb4_general_ci',
);

$CFG->wwwroot   = 'https://staging.learn.tiddalik.com.au';
$CFG->dataroot  = '/home/bitnami/moodledata';
$CFG->admin     = 'admin';

$CFG->directorypermissions = 0777;

require_once(__DIR__ . '/lib/setup.php');

// There is no php closing tag in this file,
// it is intentional because it prevents trailing whitespace problems!
```





**See also::** 

### Links to this note:
```query
"[[config.php file for learn Moodle]]"
```

