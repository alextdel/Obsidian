**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #
permissions #folders #directories #Moodle 

# Moodle folder permissions

**Created:**  23 December 2022 at  15:54 hours.

___
### Note:

Moodle's recommended ownership and [permissions for the moodledata folder is here](https://docs.moodle.org/35/en/Security_recommendations#Running_Moodle_on_a_dedicated_server)

Permission settings that allow scripts to run from the normal user's home folder to moodledata to enable the *climaintenance.html* method of entering maintenance mode. See here [[MoodleData Permissions to run  scripts]]

-----------------------

The Bitnami LMS notes give good guidance as to the correct  permissions for setting up Moodle.
Typical issues that permissions fix include
- Update buttons on the Moodle web interface - ie. plugin updates - if they do not show then often it is a folder permission issue
- Plugin installation and update buttons missing - this is a folder permission issue

#### See this procedure

***NB:***
The Bitnami folder location is not the same as the Tiddalik Learn web folder. Check the correct Moodle folder for the precise installation used - 
In the case of learn.tiddalik and staging.learn.tiddalik the web folder is
- ***~/htdocs***  which is *linked* to ***/opt/bitnami/apache2/htdocs***

The following is unedited from : [Bitnami Moodle Upgrade Doc](https://docs.bitnami.com/general/apps/moodle/administration/upgrade/)

---

# Upgrade Bitnami LMS powered by Moodle(TM) LMS

---
NOTE: We are in the process of modifying the file structure and configuration for many Bitnami stacks. On account of these changes, the file paths stated in this guide may change depending on whether your Bitnami stack uses native Linux system packages (Approach A), or if it is a self-contained installation (Approach B). To identify your Bitnami installation type and what approach to follow, run the command below:

```
> test ! -f "/opt/bitnami/common/bin/openssl" && echo "Approach A: Using system packages." || echo "Approach B: Self-contained installation."
```
The output of the command indicates which approach (A or B) is used by the installation, and will allow you to identify the paths, configuration and commands to use in this guide. [Refer to the FAQ for more information on these changes](https://docs.bitnami.com/general/faq/get-started/understand-upcoming-changes/).

---

It is strongly recommended that you create a backup before starting the update process. If you have important data, it is advisable that you create and try to restore a backup to ensure that everything works properly.

Upgrade Bitnami LMS powered by Moodle(TM) LMS following these steps, depending on your installation type:

### Approach A: Bitnami installations using system packages

-   Move your current Moodle LMS files:
    
    ```
    sudo mv /bitnami/moodle /bitnami/moodle.backup
    ```
    
-   Download the [new Moodle LMS version from the Moodle website](https://download.moodle.org/releases/latest/). Do this by clicking the package download link on the Web page or using the command below with a direct download URL (the VERSION placeholder in the command refers to the Moodle LMS version number).
    
    ```
    wget http://download.moodle.org/download.php/direct/stableVERSION/moodle-latest-VERSION.y.tgz
    ```
    
-   Create a new folder and uncompress the files:
    
    ```
    sudo mkdir /bitnami/moodle
    sudo tar -xzvf moodle-latest-VERSION.tgz -C /bitnami/moodle --strip 1
    ```
    
-   Copy your previous configuration file and your modules or themes:
    
    ```
    sudo cp -a /bitnami/moodle.backup/config.php /bitnami/moodle/
    sudo cp -a /bitnami/moodle.backup/theme/MY_THEME /bitnami/moodle/theme/
    sudo cp -a /bitnami/moodle.backup/mod/MY_MOD /bitnami/moodle/mod/
    ```
    
    > NOTE: Replace the MY_THEME and MY_MOD placeholders with the directory or path names for your downloaded and installed themes and modules (these are different from the ones shipped by Bitnami).
    
-   Configure file permissions as follows:
    
    ```
    sudo chown daemon:daemon -LR /opt/bitnami/moodle
    sudo chmod -R g+rwX /opt/bitnami/moodle
    sudo chown root /opt/bitnami/moodle/config.php
    sudo chmod 640 /opt/bitnami/moodle/config.php
    ```
    
-   Execute the following commands to check that the file permissions were configured properly:
    
    ```
    ls -la /opt/bitnami/moodle/
    ls -la /opt/bitnami/moodle/blocks/
    ```
    
    The output should reflect that the files and directories listed are owned by the _daemon_ user and _daemon_ group.
    
-   Navigate to the application from a browser and follow the steps to upgrade the database to the latest version.
    
    > NOTE: If you want to install modules or plugins from the Moodle administration panel, refer to the [migration steps](https://docs.bitnami.com/general/apps/moodle/administration/migrate/).
    

### Approach B (Self-contained Bitnami installations

-   Move your current Moodle LMS files:
    
    ```
    sudo mv /opt/bitnami/apps/moodle/htdocs/ /opt/bitnami/apps/moodle/htdocs.backup
    ```
    
-   Download the [new Moodle LMS version from the Moodle website](https://download.moodle.org/releases/latest/). Do this by clicking the package download link on the Web page or using the command below with a direct download URL (the VERSION placeholder in the command refers to the Moodle LMS version number).
    
    ```
    wget http://download.moodle.org/download.php/direct/stableVERSION/moodle-latest-VERSION.y.tgz
    ```
    
-   Create a new folder and uncompress the files:
    
    ```
    sudo mkdir /opt/bitnami/apps/moodle/htdocs/
    sudo tar -xzvf moodle-latest-VERSION.tgz -C /opt/bitnami/apps/moodle/htdocs/ --strip 1
    ```
    
-   Copy your previous configuration file and your modules or themes:
    
    ```
    sudo cp -a /opt/bitnami/apps/moodle/htdocs.backup/config.php /opt/bitnami/apps/moodle/htdocs/
    sudo cp -a /opt/bitnami/apps/moodle/htdocs.backup/theme/MY_THEME /opt/bitnami/apps/moodle/htdocs/theme/
    sudo cp -a /opt/bitnami/apps/moodle/htdocs.backup/mod/MY_MOD /opt/bitnami/apps/moodle/htdocs/mod/
    ```
    
    > NOTE: Replace the MY_THEME and MY_MOD placeholders with the directory or path names for your downloaded and installed themes and modules (these are different from the ones shipped by Bitnami).
    
-   Configure file permissions as follows:
    
    ```
    sudo chown bitnami:daemon -R /opt/bitnami/apps/moodle/htdocs/
    sudo find /opt/bitnami/apps/moodle/htdocs/ -type f -exec chmod 664 {} \;
    sudo find /opt/bitnami/apps/moodle/htdocs/ -type d -exec chmod 775 {} \;
    ```
    
-   Navigate to the application from a browser and follow the steps to upgrade the database to the latest version.
    
    > NOTE: If you want to install modules or plugins from the Moodle administration panel, refer to the [migration steps](https://docs.bitnami.com/general/apps/moodle/administration/migrate/).

---

**See also::** 

### Links to this note:
```query
"[[Moodle folder permissions]]"
```

