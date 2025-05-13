**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #SSH #Linux #servers #AWS #terminal #windows

# SSH Connecting to AWS Instance

**Created:**  21 September 2022 at  09:42 hours.

___
### Note:

### Linux version (Pop OS)
>See below for Windows [[SSH Connecting to AWS Instance#Windows SSH Version]]
 
 To connect to an instance using SSH there are two options
1. Use Putty
   Putty has a problem with using .pem files provided from AWS. See the .pem to .ppk conversion using [[Convert SSH key file from pem to ppk using puttyGen]]
   1. Set up a Putty connection using the .ppk file specified under the *Connection>SSH> Auth* file selection
   2. Once the file is selected and loaded, save the config for next time
      ![[Putty Config Linux SSH.png]]
2. Use the Pop OS (Ubuntu) terminal
	1. Enter into a terminal the following command
	   	   ``` ssh -i LightsailDefaultKey-ap-southeast-2.pem bitnami@13.54.70.251 	```
	2. Right click and select run on the .sh file - for example
	   ![[Run SSH Key shell script.png]]

		
### Windows SSH Version
>See above for Linux version [[SSH Connecting to AWS Instance#Linux version Pop OS]]

Windows can use a wide range of SSH clients. The one demonstrated by [Mukesh's Techspace - AWS Lightsail for Beginners - Pt 3](https://www.youtube.com/watch?v=l_VpA3cmXRg) is SmartTTY

**See also::** 

### Links to this note:
```query
"[[SSH Connecting to AWS Instance]]"
```

