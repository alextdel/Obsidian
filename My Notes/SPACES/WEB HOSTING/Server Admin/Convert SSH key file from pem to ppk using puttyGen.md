**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #SSH #Putty #AWS #servers #Keys 

# Convert SSH key file from pem to ppk using puttyGen

**Created:**  21 September 2022 at  08:18 hours.

___
### Note:
When running Putty or another SSH using the AWS provided keys, an error message will be given saying that the ***.pem*** file is an older type of file. This will require the .pem file to be converted to another type such as an ***.ppk*** file.

Follow these instructions - found at https://www.puttygen.com/convert-pem-to-ppk

> ### Converting .Pem to .Ppk on Unix or Linux
To convert the file on Unix is far simpler than Windows. Users are first required to install PuTTY application on their Unix machines. Once done, all a user must do is enter a one-line command. First, run the [PuTTYgen command](https://www.puttygen.com/ssh-commands) and type the below-written command:
_$ sudo puttygen pemKey.pem -o ppkKey.ppk -O private_

#### General SSH PuttyGen information 
here:: https://www.ssh.com/academy/ssh/putty/linux/puttygen

**My Example:**
I did this on an AWS file called *LightsailDefaultKey-ap-southeast-2.pem*
using this command line instruction - 
```
alex@pop-os: puttygen LightsailDefaultKey-ap-southeast-2.pem -o LightsailppkKey.ppk -O private
```

Now this .ppk file can be used with the linux version of Putty.

**See also::** [[SSH Connecting to AWS Instance]]

### Links to this note:
```query
"[[Convert SSH key file from pem to ppk using puttyGen]]"
```

