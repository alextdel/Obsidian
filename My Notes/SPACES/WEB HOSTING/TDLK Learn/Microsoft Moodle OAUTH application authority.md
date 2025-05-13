**up::** [[TIDDALIK Web MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Authorisation #Moodle #Microsoft #Azure #OAuth2

# Microsoft Moodle OAUTH application authority

**Created:**  12 September 2022 at  15:28 hours.

___
### Note:

See here for instructions. [OAuth 2 Microsoft service - MoodleDocs](https://docs.moodle.org/400/en/OAuth_2_Microsoft_service)

The following is set up in Azure using the Office 365 login we all use for the TiddalikServices Office account

### Application (client) ID
3d03047d-3647-4b88-ba2c-855d4611971c

### Client Secret (password)
Hfq8Q~94YcNhite82kQR4nM3RQICJvQn2gsw5avd

### Secret ID
370288da-f866-4e1f-96c0-c2e8c5bbc250

## In Moodle
the setup in Moodle for the OAuth2 service
This is currently for internal services only.
Could be opened up to be used for logins later.

The Authenticat token requests via HTTP headers can be ticked - check the information using the (?)
The Service base URL is currently
https ://login.microsoftonline.com/c52dba5f-1f39-4f55-8a22-d731b2f58e60/v2.0
but you get this from the Azure Active Directory app registration page - look at Overview then the Endpoints tab
![[Moodle Microsoft oauth2 settings.png]]



### OAUTH system user 
This is a user in Moodle who is used to set up the link to the Microsoft OAUTH application 
oauth_system_user


**See also::** 

### Links to this note:
```query
"[[Microsoft Moodle OAUTH application authority]]"
```

