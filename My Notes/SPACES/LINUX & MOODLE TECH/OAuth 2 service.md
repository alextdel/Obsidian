**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #Moodle #App #Azure #OAuth2 
# OAuth 2 service

**Created:**  16 March 2024 at  17:51 hours.
___
### Note:
The learn.tiddalik.com.au site (production) has an OAuth credential used for connecting the Tiddalik custom Moodle App.

In March 2024, this credential needed renewal - here are the details
1. dev.learn.tiddalik.com.au Email text:
> The refresh token for one of the OAuth services Microsoft on your site *https://dev.learn.tiddalik.com.au* has expired. This will limit the functionality of any plugins that use this service. To fix this issue, visit the OAuth 2 Services configuration page and click on the "Connect system account" icon in the table row for this service. Be sure to login using the same service account for the OAuth system each time.
> Notice produced by Microsoft when using the emailed link sent to tiddalikservices email address

2. staging.learn.tiddalik.com.au Email text:
		Same as above in 1.
**Note** - *(+++)* No learn.tiddalik.com.au Email text was recieved as, at the time of these emails in 1. and 2. the production site was running on an older version of Moodle and did not have the SMTP mailing link set up and so was not sending emails.

3. When attempting to use the staging.learn.tiddalik.com.au OAuth 2 setting page link this was seen in the browser ...
![[Pasted image 20240316175502.png|500]]

4. Visited Microsoft Azure administration pages via the Microsoft 365 administration console links and then found the Microsoft Azure App Registrations console.
5. *Microsoft Azure App Registrations*
	Direct Link:  https://entra.microsoft.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade/quickStartType//sourceType/Microsoft_AAD_IAM?Microsoft_AAD_IAM_legacyAADRedirect=true
![[Pasted image 20240316181128.png|650]]

6. The Application credential (certificates and secrets) needed to be reviewed. This involved finding the settings for
		**Application (Client) ID** -> *3d03047d-3647-4b88-ba2c-855d4611971c*
		(this ID is the main reference for the application and remained unchanged)
	Then: 
	1. Create a new Client secret
	2. Delete the outdated secret
![[Pasted image 20240316181457.png|650]]

**Description** -> *Moodle learn_tdlk production* (I typed this in the new (+) client secret field)
**Client Secret Value** -> *tWs8Q~1.l-vqNoRyG8s3p7VF6Y13MOWwxxQefcrI*
	OLD value which was deleted ... ~~Hfq8Q~94YcNhite82kQR4nM3RQICJvQn2gsw5avd~~
	**NB.** I then changed this in Moodle in the "Client secret" field of the OAuth 2 settings.
**Secret ID** -> 618d977e-5403-4dff-93e3-79ba651836d1 

-----------
> This credential is changed in the staging server only and will follow the cloning of the staging server code into the production code where it will be live. The Moodle app may need to be retested and reviewed prior to usage with clients.
___
See nota above about why the production server didn't spawn a renewal email ...see *(+++)*


**See also::** 

### Links to this note:
```query
"[[OAuth 2 service]]"
```

