**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #SSL_certificate #security  #servers #Bitnami #AWS #Lightsail 

# SSL Certificate - Bitnami

**Created:**  21 September 2022 at  10:39 hours.

___
### Note:
Before starting, the Bitnami tool assumes that you have:
- Deployed a Bitnami application and the application is available at a public IP address so that the Let’s Encrypt process can verify your domain.
- The necessary credentials to log in to the Bitnami application instance.
-  A registered domain name (or sub-domain).
- Configured the domain name’s DNS record to point to the public IP address of your Bitnami application instance.

See [Generate and Install a Let's Encrypt SSL Certificate for a Bitnami Application](https://docs.bitnami.com/aws/how-to/generate-install-lets-encrypt-ssl/) for a summary or more detailed info about the Bitnami HTTPS Config tool at [Learn about the Bitnami HTTPS Configuration Tool](https://docs.bitnami.com/aws/how-to/understand-bncert/)


AWS along with most VPS providers will use the Let's Encript CA.

The Bitnami HTTPS Configuration tool is included in all Bitnami images (except two that are mentioned at the page linked above). Set up SSL with default setting -  

Run the HTTPS config tool using the instructions at [Learn about the Bitnami HTTPS Configuration Tool](https://docs.bitnami.com/aws/how-to/understand-bncert/)

Using Filezilla transfer (download)
- the log file ( /tmp/bncert-XXdatetimeXX.log) as listed in output from the SSL process just completed. 
- the account settings record as listed in the log file (at */opt/bitnami/letsencrypt/accounts*)

**See also::** 

### Links to this note:
```query
"[[SSL Certificate - Bitnami]]"
```

