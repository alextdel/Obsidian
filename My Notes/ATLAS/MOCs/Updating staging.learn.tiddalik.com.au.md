**up::** {enter link to appropriate MOC}
**index::** [[+Index for Personal]]

**tags::** #TDLK_Learn #Moodle #update 

**Created:**  06 May 2025 at  19:57 hours.
___
## Update process
### Introduction
As of 2025, the Tiddalik Learn **staging** server at [staging.learn.tiddalik.com.au](https://staging.learn.tiddalik.com.au) is running a trial Moodle 4.5 version installation. This is for testing only.

**NB** - The payment method plugin used in Nahri Learn should be thoroughly tested prior to the main learn.tiddalik.com.au or learn.nahri.com.au moodle sites being upgraded from the 4.4 branch to the newer 4.5 branch.

**Refreshing the staging server** - The best process for refreshing the staging server is to 
1. Update the learn.tiddalik.com.au site including:
	- plugins
	- themes (_Edwiser_)
	- Moodle codebase - currently managed using *git*.
		- check no users are currently logged in
		- log in to server (use ssh from terminal or putty etc)
		- `su` to the appropriate domain user
			- users are 
				- **tiddalikadmin** is user for both *learn.tiddalik.com.au* and *staging.tiddalik.com.au*
				- **nahrilearn** is the user for *learn.nahri.com.au*
			 ==Passwords are in Bitwarden under the Servers and VMs category== 
		- activate maintenance mode
		```
		$> cd ../../public_html/admin/cli
		$> php maintenance.php --enable		
		```
		-  check and pull the latest git version for the branch
		```
		$> cd ../../public_html
		$> git status 
		#ignore unstaged & untracked files (plugins/themes)
		$> git pull
		```
		- now perform the  upgrade
		```
		$> cd ../../public_html/admin/cli
		$> php upgrade.php # answer yes 'y' when asked
		```
		- now deactivate maintenance mode
		```
		$> php maintenance.php --disable
		```
	- Log in to Moodle as admin - see Bitwarden for Admin01 user/
	- Check 


2. Backup
	- the Moodle database - use the command line or MySQLAdmin,
	- the `/moodledata` folders and files - check the link above for details on which folders and file do and do not need preserving
	- the `config.php` - this may need editing in the case of a new database or moodledata file location relative to the Moodle code.
	- all the moodle site files (usually in `/path/to/domain/learn.tiddalik.com.au/public_html/...`) including the `.git` directory and the newly updated plugin and theme files.
	- 
3. Install the same branch and version of the Moodle installation in the staging server location
4. Install the same set of plugin files 
- Update the plugins and base code to the latThe database, plugin state, settings, moodledata folders and files (check which are required here) and any other custom work from learn.tiddalik.com.au  must be migrated to 



**See also::** 

### Links to this note:
```query
"[[Updating staging.learn.tiddalik.com.au]]"
```

