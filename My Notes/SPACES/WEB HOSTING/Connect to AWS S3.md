**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #AWS #S3 #command_line #backup 

# Connect to AWS S3

**Created:**  10 May 2023 at  14:27 hours.

___
### Note:

#### Setup S3 bucket
1. Set up a new S3 data store for testing backups - **DONE**
	- tdlk-store1-version1.0

#### Setup AWS Access Key
1. Set up an AWS Access Key - (**Current keys are in AWS IAMs record in BitWarden**)
	- eg (old examples - ***do not use***)
	  Key - *AKIAV2G2SELNGXDTA467*
	  Secret Key - *uqNneyGeAKICYPMvU2sVfRH5E0963CJ8f2pY6W9I*
		- csv containing these - (***current csv in IAMs record in BitWarden***)... 

#### Setup AWS CLI command if required
**As of 2023 Q3 Bitnami was using AWS CLI 1, which works**
1. Downloaded and installed the AWS CLI 2 tool so that I can connect to the S3 instance using my computer CLI
	- instructions for [install of AWS CLI version 2 here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)... 

#### Test by copying a file
1. Tested with a directory upload through the AWS S3 bucket interface
2. Tested with a CLI copy
```
$ aws s3 cp test.s3test s3://tdlk-store1-version1.0/
```

Response was ...
```
upload: ./test.s3test to s3://tdlk-store1-version1.0/test.s3test
```


**See also::** 

### Links to this note:
```query
"[[Connect to AWS S3]]"
```

