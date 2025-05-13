**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #Moodle #smtp #AWS #SES 
# Moodle - AWS SES SMTP

**Created:**  14 March 2024 at  14:46 hours.
___
### Note:
This is for when a Moodle installation has been created on an AWS lightsail Bitnami server.

1. Use the AWS SES console to gain access to the regions SMTP service - something like "email-smtp.ap-southeast-2.amazonaws.com"
2. Verify the domain and email addresses (from addresses) - domains will need CNAME entries added to the DNS of the domain (eg. GoDaddy)
3. Create SMTP credentials - this effectively creates an IAM user
	1. Save the credentials 'IAM user name', 'SMTP-user name', 'SMTP password' - note the **SMTP user name** and **SMTP password** are the credentials needed for Moodle to use.
	2. Allocate the Permission policy ***AmazonSesSendingAccess*** to the SMTP user.
4. Installing **swaks** on the server will allow basic email testing to make sure ports etc are correct. Once installed the command is
```shell
swaks --from="a verified email address such as noreply@moodle.com.au" \
--to="a test email address like 123.adelaforce@gmail.com" \
--server="the aws smtp server ie. email-smtp.ap-southeast-2.amazonaws.com"  \
--port="such as '587' for TLS" \
--auth  \
--auth-user="the SMTP user name eg 'ABCDEFGHIJKLMNOPQ'"  \
--auth-password="the SMTP password eg 'BJT0+ccV1hXXXXXXXXe69y5q8rf'" \
--tls
```

5. The **swaks** command line confirms the *server -> smtp* connection including network/port/authentication. The Moodle test email function can then be used under ***Site administration > Server > Outgoing mail configuration*** page.
	a. **Note** - if the test email function fails try the **Email configuration test** plugin
6. **Email configuration test plugin** - this is a useful plugin to install. It may: 
		1. Show success when the Moodle test email function fails
		2. Actually cause the Moodle test email function to start working though it failed previously - don't know why?
 7. If the config.php file was changed to show debug messages in the log file - don't forget to go back and comment out the debug lines.  


**See also::** 

### Links to this note:
```query
"[[Moodle - AWS SES SMTP]]"
```

