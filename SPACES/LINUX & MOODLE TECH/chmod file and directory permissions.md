**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Linux #commands #permissions #CLI #chmod #find

# chmod file and directory permissions

**Created:**  05 April 2023 at  20:34 hours.

___
### Note:
A common permission pattern is 
- 644 for files 
  user = `r w -`
  group = `r - -`
  others = `r - -`
- 755 for directories
  user = `r w x`
  group = `r - x`
  other = `r - x`

The [`chmod`](https://linuxize.com/post/chmod-command-in-linux/) command allows you to change the permissions of files using symbolic or numeric mode.
```sh
chmod -R MODE DIRECTORY
```

e.g.
```sh
chmod -R 755 /var/www/html # (this is the numeric mode)
chmod -R u=rwx,go=rx /var/www/html # (this is the symbolic mode)
```


The [`find`](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/) command is useful when differentially assigning permissions to directories (e.g. 755) and files (e.g. 644)
```sh
#these use the numeric mode
find /var/www/html -type d -exec chmod 755 {} \;
find /var/www/html -type f -exec chmod 644 {} \;
# these use the symbolic mode
find /var/www/html -type d -exec chmod u=rwx,go=rx {} \;
find /var/www/html -type f -exec chmod u=rw,go=r {} \;

```

The [`find`](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/) command searches for files or directories under `/var/www/html` and passes each found file or directory to the `chmod` command to set the permissions.

Hint for processing many file ...
When using `find` with `-exec`, the `chmod` command is run for each found entry. Use the [`xargs`](https://linuxize.com/post/linux-xargs-command/) command to speed up the operation by passing multiple entries at once:

```
find /var/www/html -type d -print0 | xargs -0 chmod 755 
```

**See also::** 

### Links to this note:
```query
"[[chmod file and directory permissions]]"
```

