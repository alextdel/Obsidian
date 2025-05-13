**up::** [[Git MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #git #restore #checkout

# Git Notes

**Created:**  07 January 2023 at  12:26 hours.

___
### Note:
When checking a cloned git project to find if any files are missing ... first enter the project folder
	```cd htdocs```
then ...
- use git ***checkout*** without any additional operators to check for any differences between the local copy and the main online git repo
	```git checkout```
OR
- for detailed status of the local repo (project folder), enter the folder then use the ****git status*** command
	```git status```
sample output - note shows files that have been included in the project folder but not checked in (in the case of moodle specific)
![[Git status.png]]

this tells me that I have a directory *testdir/* and a file *testfile.php* that I have included but are not currently added to my local git repo - the response to status also tells me how to add these items if I would like.
Also tells me the file or folders that are deleted eg. *index.php* which I deliberately deleted for a test.
To restore the deleted items use the ***git restore*** command
	```git restore index.php```
for example
![[Git restore and status.png]]


**See also::** 
![[Git MOC#Link to Permanent Notes]]

### Links to this note:
```query
"[[Git Notes]]"
```

