**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Moodle #update #Edwiser #plugins #filters #local_plugins 

# Moodle Update Notes

**Created:**  29 December 2022 at  18:25 hours.

___
### Note:
See [[SPACES/LINUX & MOODLE TECH/Moodle Update using Git]] for a possible streamlines approach which involves setting the ~/htdocs folder as a git local repo, cloning the remote (Moodle Github repo) repo, thus giving the ability to do minor updates very easily with git.

***The method here is the non-git method ...***

---

### The Moodle Update Process (non-git version)

***NB - Inform users that update will be occurring and let them know the time/date etc and how long the system is likely to be offline - if possible after hours***

1. *Read the Moodle release and preliminary requirements information*
2. Update all plugins to the most recent version relating to current (pre-update) Moodle version prior to update - check Moodle Administration Manage Plugins.
3. Make a copy of the Moodle web files -
	- Can be done with a move command
	  ```sudo mv /opt/bitnami/apache2/htdocs /opt/bitnami/apache2/htdocs.backup```
	  OR
	  - Can be done with a copy command
	    ```sudo cp -a /opt/bitnami/apache2/htdocs /opt/bitnami/apache2/htdocs.backup``` 
4. Make a copy of the Moodledata directory (not really necessary but just in case)
    ```sudo cp -a /home/bitnami/moodledata /home/bitnami/moodledata.backup```
5. Backup the Database or make sure a snapshot has  been recently taken and then ...
6. Place the Moodle instance into Maintenance mode so that no further database updates are  possible while the update takes place.
7. Obtain the new version Moodle files by either:
	- Downloading the required update to the local computer and transfer to the server using FileZilla **e.g.** moodle-latest-XXX.tgz
	  OR
	- use WGET with the direct link (note the Moodle webpage link is not direct and will not give a satisfactory download - if in doubt use the FileZilla method)
        ```wget http://download.moodle.org/download.php/direct/stableVERSION/moodle-latest-VERSION.y.tgz```

8. Unzip using the tar utility into a correctly named folder (the htdocs folder usually)
	```tar xvzf moodle-latest-XXX.tgz ```
	- will probably need to rename the directory by using the move command in linux (mv).

### Reinstating the Edwiser theme, blocks, filters and local plugins

9. Copy across from backed up Moodle htdocs files
	1. The Edwiser theme - in **theme** directory
	   - *remui* directory needs to be copied across
	2. The Edwiser blocks - in **blocks** directory these directories need copying across
	   - *edwiser_grader*
	   - *edwiseradvancedblock*
	   - *edwiserratingreview*
	3. The Edwiser filters - in **filter** directory this directory needs copying across
	   - *edwiserpbf*
	4. The Edwiser local plugins - in **local** directory these directories need copying across
	   - *edwiserpagebuilder*
	   - *edwisersiteimporter*
	   - *remuihomepage*
10. Follow the [Bitnami LMS server update instructions here](https://docs.bitnami.com/virtual-machine/apps/moodle/administration/upgrade//) (or the note here [[SPACES/LINUX & MOODLE TECH/Moodle folder permissions]]) to set the permissions for the folders and files and the specific permissions and group owners for the *config.php* file - check with the [Moodle pages here](https://docs.moodle.org/400/en/Security_recommendations#Most_secure.2Fparanoid_file_permissions) which give up-to-date security information for each version (check appropriate version is selected.)
11. With new code and plugins copied across the Moodle webpage can now be accessed. The upgrade process will highlight any errors or required updates i.e. plugins that need updating prior to database update etc.
12. Follow the on page prompts and work through the steps indicated one at a time - refresh the information page each time.
13. Once everything is satisfactory, reset (disable) the Maintenance mode and test the site. 

*Check the note on **[[SPACES/LINUX & MOODLE TECH/Moodle Maintenance Mode]]** if you have problems with a white page following the process or if disabling the maintenance mode does not work.*
 
---
If not already done, now check for further updates to Edwiser for the new version. 

**See also::** [[SPACES/LINUX & MOODLE TECH/Moodle Update Notes]], [[SPACES/LINUX & MOODLE TECH/Moodle Update using Git]], [[SPACES/LINUX & MOODLE TECH/Moodle folder permissions]]

### Links to this note:
```query
"[[Moodle Update Notes]]"
```

