**up::** [[My Vault/ATLAS/MOCs/Git MOC|Git MOC]]
**index::** [[+Index for Personal]]
 

**tags::** 

# Git by Jesse Liberty

**Created:**  24 October 2023 at  14:06 hours.

___
### Note:
1. Most things happen locally on the machine
2. Parts of the GIT landscape
	1. Work area
	Current files in current directory. Shows one version of the files at a time.
	3. Staging (Index)
	Holds files you want to commit or new files you want to add. 
	5. Repo on your machine
	Holds all the versions of your files - everything.
	7. Remote Repo
	Repo in the cloud eg. GitLab, GitHub etc.
	9. Stash
	Holds modifications you don't want to use now, but don't want to lose.
3. **Commit** <--> **Checkout** take work area and put into repo in local machine or take repo version and put into the work area
   ![[Pasted image 20231024143353.png|500]]
	- Commit message - meaningful message that is specific, be specific.
	- You can up messages with **interactive rebase** if required.
	- Each commit points to its  parent  eg. 
	![[Pasted image 20231024142109.png|500]]
	  
4. **Push** - take local repo and push up to the cloud
5. **Head** - points to the tip of a branch.
6. **Main** - all development is done on branches - never on *main*
7. Create a branch
   `>> git checkout main
   `>> git branch feature_name
   `>> git checkout feature_name`
   OR
   `>> git checkout -b feature_name` 
	 -  When you checkout a branch the Head points to the last commit state for the branch
 8. **Merge** - takes a branch commit and merges the work into another branch eg. merge to main.
	 - in a  team environment you wouldn't Merge immediately but you would issue a **Pull Request**. Once approved the merge would occur.
 9. Fast-forward merge - if the main branch or parent branch has not progressed since the feature branch has been worked on, a fast-forward merge is possible.
    ![[Pasted image 20231024143956.png|500]]
 10. Rebase - can be helpful if the main branch has progressed while the feature branch work has been happening. Rebase takes a copy of the feature commits and places  them on top of the last commit of main. Feature branch then has  all the changes of main included.
     ![[Pasted image 20231024144436.png|250]]--![[Pasted image 20231024144524.png|250]]
- Advantages of rebasing
	 a. much cleaner history
	 b. reduces conflicts - commit and rebase frequently
- **Never Rebase on the Server**
- Remember - you rebase onto another branch
		`>>git checkout feature_name`
		`>>git rebase main` 
11.  **Interactive Rebase** - not really a rebase - allows you to squash together a series of commits and reword the messages - *you do this before Pushing to server* `>>git rebase -i`
12. **Commit - amend** command - if a commit has been done and needs correcting and have not pushed it yet `>> git commit -amend`
    If not the most recent commit, use *rebase interactive*
13. Aliasing - allows shorthand commands to be set up.
	1. to edit existing aliases or add in bulk - `>> git config --edit --global`
	2. to add individual aliases
	   ![[Pasted image 20231024150743.png|300]]
14. Log
    The following log commands can be used
![[Pasted image 20231024151046.png|500]]
15. Other useful commands - restore, show, blame, diff
    ![[Pasted image 20231024151211.png|500]]
- `git restore .` will return you to the last commit and discard all changes done to the file(s) since the last commit - **careful**, you *will lose* all work since the commit.

**See also::** [[git]]

### Links to this note:
```query
"[[Git by Jesse Liberty]]"
```

