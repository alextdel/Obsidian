``**up::** [[Git MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #git #website #servers #update #Moodle 

## Set up existing web installations for GIT(convert from non-git method)

**Created:**  10 January 2023 at  17:11 hours.

--- 
### Note:
Following assumes using the Bitnami LAMP server for *staging.* or *learn.* Tiddalik website.

*The command line version of Git is discussed here. There are GUI apps but these are mainly unnecessary.*

---

### A. Set up existing web installations for GIT(convert from non-git method)

**In this note we will set up an existing Moodle installation to start using GIT 
In our example this is from the *'~/htdocs'* folder.**

A version of this can be found from Moodle's [Git for Administrators page](https://docs.moodle.org/400/en/Git_for_Administrators) 
This has been modified below for Tiddalik's current installation of Moodle and using information from [Wise Cat's YouTube tutorials](https://www.youtube.com/@Wise-Cat).

#### Git Sources
When cloning from a public GIT repository two sources can be commonly used:
	1. a transfer using the ***git://*** protocol eg. git clone git://git.moodle.org/moodle.git
	2. a transfer using ***https://*** protocol eg. https://github.com/moodle/moodle.git
Both work but the git protocol uses a readonly transfer protocol on Port 9418. The `git://` protocol is faster.ls

> ***Note*** *-- Port settings for AWS Lightsail and GitHub*
> I have set up a git clone without the additional port setting but just in case.
> 
> When cloning into a Bitnami LAMP server set up on Lightsail the git clone "git://git.moodle.git ." command may not work as the firewall does not include the required port 9418 opened.
> 
> So, in AWS LIghtsail the readonly port that github uses will need to be added to the instance firewall - see image for  `Custom TCP 9418 Any IPv4Address`.
>    ![[AWS Lightsail GIT port setting.png]]
> 

#### How to control where the cloned git files go.

The *git clone* command can place the repository files in
		- the default location ie. moodle
			 ``` git clone git://git.moodle.org/moodle.git```
		- a specific folder ie. www_from_git
		  	 ``` git clone git://git.moodle.org/moodle.git www_from_git```
		- the folder from which the command is run 
		    	 ``` git clone git://git.moodle.org/moodle.git .```
		***note the trailing '.' dot which means "this folder"**
		
***NB:***
GIT cannot clone into a folder that is not empty. Even a folder that has contents deleted will sometimes have the . (self) and .. (parent links) seen as being non empty. Solution is to 
1. delete the parent folder
2. remake the folder 
3. set correct permissions for the folder
4. cd into the folder
5. then use the command as above 
```
git clone git://git.moodle.org/moodle.git .  
```

ote:cd

-----------------------

> **Using symbolic links with git and  web servers**
> 
> See here for [[Using GIT and symbolic links]] - this is based on Wise Cat's video (below) on using symbolic linked directories.
 

These notes show how to locate the git cloned files into the *~/htdocs* folder and not a sub-folder.  e.g. enter the project folder `$ cd ~/htdocs`, then use git to clone into this folder and not a subfolder.
i.e. ![[git command1.jpg]]

___

1. Check the official Moodle git repository at [git://git.moodle.org/moodle.git](git://git.moodle.org/moodle.git) (with an official clone at [git://github.com/moodle/moodle.git](git://github.com/moodle/moodle.git)).

2. Make sure *git* system is installed on the server
   `$ sudo apt install git`
3. To initialize local checkout into the *~/htdocs/* folder, use
	`$ cd /path/to/your/webroot`
	ie. ***$ cd ~/htdocs***
4. Clone the git repo into the local folder 
	`$ git clone git://git.moodle.org/moodle.git .           (1)`

> if we weren't using the dot notation as shown in the step above, we would at this point move into the directory that was made by the git clone command e.g. *$ cd moodle*. However, we are using the htdocs folder for the parent of the cloned repo.

5. list all the available branches from the repo just cloned ...
	`$ git branch -a                                       (2)`

6. tell git which branch we want to use (track), in our case version 4 stable 
	`$ git branch --track MOODLE_400_STABLE origin/MOODLE_400_STABLE(3)`

7. now checkout the version for use - this will now be the file set that we see in ~/htdocs
	`$ git checkout MOODLE_400_STABLE                  (4)`

See notes `(1)(2)(3)(4)` below

> - The command `(1)` initializes the new local repository as a clone of the 'upstream' (i.e. the remote server based) moodle.git repository. The upstream repository is called 'origin' by default. By default the *clone* command creates a new directory named _moodle_, where it downloads all the files. To download into the current folder without making a subdirectory use the dot as explained above.
> - This operation can take a while as it is actually getting the entire history of all Moodle versions
> - The command `(2)` lists all available branches.
> - Use the command `(3)` to create a new local branch called MOODLE_400_STABLE and set it to track the remote branch MOODLE_400_STABLE from the upstream repository.
> - The command `(4)` actually switches to the newly created local branch.

---

### B. Moodle Update using Git
See **[[SPACES/LINUX & MOODLE TECH/Moodle Update using Git]]** note

---

**See also::**
- [[SPACES/LINUX & MOODLE TECH/Moodle Update Notes]]
- [[SPACES/LINUX & MOODLE TECH/Moodle folder permissions]]
- [[SPACES/LINUX & MOODLE TECH/Moodle Update using Git]]
