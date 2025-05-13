**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #moodle #maintenance #commands #CLI


# Moodle Maintenance Mode

**Created:**  17 February 2023 at  16:42 hours.

___
### Note:

*It is possible that when Moodle is put into maintenance mode it will not come out gracefully.* 

**Symptoms** - Moodle website serves a white page, a test html file placed in the htdocs folder will be served up correctly.

**Background** - The 'maintenance mode' can be triggered in a few ways
1. Through the web interface in the Server Admin pages.
2. Through the CLI of the server 
   `cd webroot/admin/cli`
   `php maintenance.php --enable `
 3. by placing a climaintenance.html file in the moodledata folder - this is served in place of the index.php file (this is the 'white' page). See [this Moodle page for version 4.1](https://docs.moodle.org/401/en/Maintenance_mode). 
 
	 - On Tiddalik's learn.tiddalik.com.au site using AWS Bitnami server the file list for moodledata looks like this when the CLI version is activated.

	![[Pasted image 20230217164631.png]]
**Solution**
1. Attempt to run the following from the CLI
    `cd webroot/admin/cli`
   `php maintenance.php --disable `
2. If this doesn't bring Moodle back to a usable state or if the above gives an error like the following 
   `!!! Coding error detected, it must be fixed by a programmer: Failed to unserialise data from file. Either failed to read, or failed to write. !!!`
   try this
	a. run `php purge_caches.php` from the same directory as in 1. above
	b. 'purge_caches.php' may also bring the same "!*!! Coding error ...*" message as in 2. If so
	- delete the cache folder manually by doing `sudo rm -R cache/` from the Moodledata directory.
	- Then run `php purges_caches.php` and then `php maintenance.php --disable` from the *webroot/admin/cli* directory.
Reload the webpage to check for correct operation.
	
**See also::** 

### Links to this note:
```query
"[[Moodle Maintenance Mode]]"
```

