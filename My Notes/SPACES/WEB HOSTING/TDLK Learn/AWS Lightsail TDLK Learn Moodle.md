**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** 

# AWS Lightsail TDLK Learn Moodle

**Created:**  25 September 2022 at  13:48 hours.

___
### Note:
# This version is about to be retired [see here](obsidian://open?vault=My%20Personal%20Vault&file=SPACES%2FMOODLE%2FMoodle%20Staging%20Server%20Setup)
1. Name of instance: TDLK_Learn_Bitnami_LAMP
2. Date started: 25 Sept 2022
3. Static IP: 13.55.208.193
   - ID: # StaticIP-TDLKLearn-Moodle
4. Bitnami application credentials: MWExjYvgb4Lb (use for applications and databased within the server)
5. Bitnami applications eg. phpMyAdmin and MariaDb are in the **//bitnami** directory
6. Moodle  and Moodledata directories created 
	1. Next step is to set [user group and permissions](obsidian://open?vault=My%20Personal%20Vault&file=SPACES%2FMOODLE%2FMoodle%20folder%20permissions). <-- see this note



### Server Configuration Notes:
#### Apache setting
see file in **/opt/bitnami/apache2/conf/httpd.conf**
1. The Apache server root directory for serving pages is
	- DocumentRoot "/opt/bitnami/apache/htdocs"
2. The User/Group that the apache httpd service runs as
	- daemon/daemon
	- 



**See also::** 

### Links to this note:
```query
"[[AWS Lightsail TDLK Learn Moodle]]"
```

