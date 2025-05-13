**up::** [[Git MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #git #website #servers #Moodle 

# Using GIT and symbolic links

**Created:**  10 January 2023 at  15:56 hours.

___
### Note:
This is an example of using symbolic links to streamline maintenance processes. 

In this we move the contents of a website directory to a backup copy location but because we haven't finished the upgrade task we use create a link so the web server still functions.

```$ mv www www_old && ln -s www_old www ```

note 1. The **&&** causes the second command *ln* to run immediately after the first *mv*.

note 2. **ln -s** is the command to create a symbolic link. 
		Syntax:: ```$ ln -s <destination> <source> ```


**See also::** [[SPACES/LINUX & MOODLE TECH/Moodle Update using Git]], [[Git MOC]]

### Links to this note:
```query
"[[Using GIT and symbolic links]]"
```

