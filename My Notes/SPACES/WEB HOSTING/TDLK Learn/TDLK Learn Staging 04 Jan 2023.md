**up::** [[TIDDALIK Web MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #TiddalikLearn #Staging #servers #database #setup_notes


# TDLK Learn Staging 04 Jan 2023

**Created:**  04 January 2023 at  17:10 hours.

___
### Note:
1. New Staging Server created:
	- Server Source Name: **STAGING_TDLK_Learn_LAMP20221008**
	  (2GB RAM, 1 vCPU, 60GB SSD)
	- Server New Name: **TDLK_LRN_STAGING_2023-01-04**
	  (2GB RAM, 1 vCPU, 60GB SSD)
		- STATIC IP created and connected - **54.66.18.60** 

2. New Staging Database  created:
- DB Source Name: **TiddalikLearn_Moodle_DB** from snapshot 11:55 3 Jan 2023
  (1GB RAM, 2vCPUs, 40GB SSD) 
- DB New Name: **TDLK_LRN_Staging_MDL_DB**
  (1GB RAM, 2vCPUs, 40GB SSD) as above

3. GoDaddy DNS
	- change staging.learn A Record to **54.66.18.60**
4. Run the Let's Encrypt app on the new server - if the email address is unknown find in this directory ` /opt/bitnami/letsencrypt/accounts/acme-v02.api.letsencrypt.org`
	  - for staging.learn.tiddalik.com.au and learn.tiddalik.com.au use
	   admin01@tiddalikservices.com.au
5. Once the server and the database are up and DNS in 3. is complete then update the config.php file ```~/htdocs/config.php```
6. Check these settings
   ![[Moodle Config_php file for TDLKLrn.png]]
	- Note 1. the database password will be new 
	- Note 2. for the AWS Lightsail databases the database type is mysql so use the **mysqli** type
   
7. don't forget to clean up - saves money
	- delete unwanted databases
	-  delete unwanted servers 
	-  decommission / delete static IPs

**See also::** [[SPACES/LINUX & MOODLE TECH/Moodle Update Notes]] 

### Links to this note:
```query
"[[TDLK Learn Staging 04 Jan 2023]]"
```

