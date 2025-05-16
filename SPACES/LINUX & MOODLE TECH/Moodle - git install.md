**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #Moodle #git #installation
# Moodle - git install

**Created:**  21 May 2024 at  11:34 hours.
___
### Note:
The Moodle documentation give this procedure: [see here](https://docs.moodle.org/404/en/Git_for_Administrators#Obtaining_the_code_from_Git)

> You can find the official Moodle git repository at [git://git.moodle.org/moodle.git](git://git.moodle.org/moodle.git) (with an official clone at [git://github.com/moodle/moodle.git](git://github.com/moodle/moodle.git)). To initialize your local checkout, use
> 
> $ cd /path/to/your/webroot
> $ git clone git://git.moodle.org/moodle.git                       (1)
> $ cd moodle
> $ git branch -a                                                   (2)
> $ git branch --track MOODLE_404_STABLE origin/MOODLE_404_STABLE     (3)
> $ git checkout MOODLE_404_STABLE                                   (4)
> 
> - The command (1) initializes the new local repository as a clone of the 'upstream' (i.e. the remote server based) moodle.git repository. The upstream repository is called 'origin' by default. It creates a new directory named _moodle_, where it downloads all the files. This operation can take a while as it is actually getting the entire history of all Moodle versions
> - The command (2) lists all available branches.
> - Use the command (3) to create a new local branch called MOODLE_404_STABLE and set it to track the remote branch MOODLE_404_STABLE from the upstream repository.
> - The command (4) actually switches to the newly created local branch.
> 

**See also::** [[Moodle Update using Git]] [[Moodle folder permissions]]

### Links to this note:
```query
"[[Moodle - git install]]"
```

