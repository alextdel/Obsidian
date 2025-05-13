**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Moodle #Git #Update 

# Moodle Update using Git

**Created:**  06 January 2023 at  15:02 hours.

___
### Note:
Following assumes using the Bitnami LAMP server for *staging.* or *learn.* Tiddalik website.

*The command line version of Git is discussed here. There are GUI apps but these are mainly unnecessary.*

- Don't forget to check the [[SPACES/LINUX & MOODLE TECH/Moodle folder permissions]] and [[SPACES/LINUX & MOODLE TECH/Moodle Update Notes]].

---

### A. Set up existing web installations for GIT

See **[[SPACES/LINUX & MOODLE TECH/Set up existing web installations for GIT]]** note

---

## B. How to update a moodle installation minor release using GIT

Check the [shortlog](http://git.moodle.org/gw?p=moodle.git;a=summary) to see if the official repository has been already updated or not. Usually updates are emailed to subscribed Moodle users.

With GIT set up, Moodle can be updated to the latest minor version of code ( as of writing on the MOODLE_400_STABLE branch). This is done like this ...:

**Reference**: ***WiseCat YouTube Video*** - [Update your Moodle with only 5 commands](https://youtu.be/9V1y7G9ssqo)

>***Note 1 -*** 
The following assumes ownership of directories and files is **daemon : bitnami**. This allows the normal user to do maintenance tasks.

>***Note 2 -*** 
WiseCat uses commands like
`sudo -u daemon php admin/cli/maintenance.php --enable`
but I found that this use of `sudo -u daemon ...` caused a critical warning when attempting to run the upgrade script. I think this is because the daemon user is more limited that the bitnami user.

1. `$ cd /path/to/your/moodle` places you within the moodle web directory i.e. /htdocs/
2. `$ sudo php admin/cli/maintenance.php --enable` run the php script 'maintenance.php' and sets the maintenance mode as **enabled** this way of enabling maintenance mode is more secure than the web way
3. `$ git pull` pulls the latest version of the currently set branch
4. `$ sudo php admin/cli/upgrade.php` run the php  script 'upgrade.php' which is the same as running the web version
5. `$ sudo php admin/cli/maintenance.php --disable` resets the maintenance  mode to off.

If this is a production site you should still consider the [Upgrade](https://docs.moodle.org/400/en/Upgrade "Upgrade") instructions (e.g. take backups).

**See also::**
- [[SPACES/LINUX & MOODLE TECH/Moodle Update Notes]]
- [[SPACES/LINUX & MOODLE TECH/Moodle folder permissions]]
- [[SPACES/LINUX & MOODLE TECH/Set up existing web installations for GIT]]

### Links to this note:
```query
"[[Moodle Update using Git]]"
```

