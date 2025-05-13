**up::** [[My Vault/ATLAS/MOCs/SERVER AND WEB ADMIN MOC|SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #aws #backup #shell_script #Lightsail #storage

# AWS bucket maintenance scripts

**Created:**  26 October 2023 at  11:20 hours.

___
### Note:
#### Script to delete storage objects in Lightsail buckets older than, say, 7 days.

```bash
#!/bin/bash

# Your bucket name and folder (prefix) if applicable
BUCKET_NAME="your-bucket-name"
FOLDER="your-folder-prefix/"

# Calculate the date 7 days ago
SEVEN_DAYS_AGO=$(date --date="7 days ago" "+%Y-%m-%dT%H:%M:%S")

# List objects in the bucket and filter those older than 7 days
OBJECTS_TO_DELETE=$(aws s3 ls s3://$BUCKET_NAME/$FOLDER | \
  awk '{print $4}' | \
  while read object; do
    LAST_MODIFIED=$(aws s3 ls s3://$BUCKET_NAME/$object --recursive | awk '{print $1, $2}')
    if [[ "$LAST_MODIFIED" < "$SEVEN_DAYS_AGO" ]]; then
      echo "$object"
    fi
  done)

# Delete the old objects
for object in $OBJECTS_TO_DELETE; do
  aws s3 rm s3://$BUCKET_NAME/$object
done
```
#### Create a file and change its metadata to say it is older than 7 days

To place an object in the Amazon Lightsail storage bucket and make it appear as if it's more than 7 days old for testing purposes, you can manually set the object's "Last-Modified" timestamp using the AWS CLI. 

1. **Create a test object**:
   You can create a simple text file as a test object:
   ```bash
   echo "This is a test object." > test.txt
   ```

2. **Upload the object**:
   Use the AWS CLI to upload the test object to your Lightsail storage bucket:
   ```bash
   aws s3 cp test.txt s3://your-bucket-name/
   ```
   Replace `"your-bucket-name"` with the actual name of your Lightsail storage bucket.

3. **Change the Last-Modified timestamp**:
   To modify the "Last-Modified" timestamp of the object to make it appear older than 7 days, you can use the `aws s3api` command with the `copy-object` operation. This operation allows you to specify the `x-amz-copy-source-if-modified-since` header to set a specific date for the "Last-Modified" timestamp.

   Here's an example of how to set the "Last-Modified" timestamp to 10 days ago for the test object:
   ```bash
   OBJECT_KEY="test.txt"
   DATE_TEN_DAYS_AGO=$(date --date="10 days ago" -u +"%Y-%m-%dT%H:%M:%SZ")

   aws s3api copy-object \
     --copy-source your-bucket-name/$OBJECT_KEY \
     --bucket your-bucket-name \
     --key $OBJECT_KEY \
     --metadata-directive REPLACE \
     --metadata Last-Modified=$DATE_TEN_DAYS_AGO
   ```
   Replace `"your-bucket-name"` and `"test.txt"` with your actual bucket name and object key.

4. **Verify the timestamp**:
   You can use the `aws s3 ls` command to verify that the "Last-Modified" timestamp of the test object has been changed to the desired date:
   ```bash
   aws s3 ls s3://your-bucket-name/
   ```
Now, the test object should appear as if it's more than 7 days old in your bucket, allowing you to test your object deletion script or any other processes that rely on object age.
```bash

```


**See also::** 

### Links to this note:
```query
"[[AWS bucket maintenance scripts]]"
```

