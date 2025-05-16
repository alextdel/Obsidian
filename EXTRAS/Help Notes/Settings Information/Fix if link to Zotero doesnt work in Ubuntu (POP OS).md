**up::** [[Help and Support List]]
**index::** [[+Index for Personal]]
 

**tags::** #Zotero_Link

# Fix if link to Zotero doesn't work in POP OS (Ubuntu)

**Created:**  04 July 2022 at  21:01 hours.

___
### Note:
When the Zotero program is installed using the normal Linux process found here 
[Linux Installation Instructions for Zotero](https://www.zotero.org/support/installation), the Linux version of Obsidian with the Citation Plugin configured will insert links from the exported Zotero library (.bib file) but the link inserted into the notes will not open in Zotero.

I found the fix to be
1. Check the registered MIME-types in the /usr/share/applications/defaults.list
- Zotero is not mentioned so the next step adds a user specific addition
2. Check the **zotero.desktop** file in the *~/.local/share/applications/* folder.
- If the installation of Zotero was followed there should be a file with the correct name **zotero.desktop** which is a hard-link to the _/opt/zotero/**zotero.desktop**_ file.
3. I ran the **update-desktop-database** command using **sudo** but I'm not sure if this made any difference
4. I edited the ***~/.config/mimeapps.list*** section "*Default Applications*" by adding the line
-  "**x-scheme-handler/zotero=zotero.desktop**"

As soon as I did this the links in Obsidian then worked

### References:

[Zotero installation instructions](https://www.zotero.org/support/installation)

Points 1 to 3 above came from carefully reading and using this askubuntu post by  [Pablo Bianchi's](https://askubuntu.com/a/1023143). I used his points 1, 2(check only as the .desktop file link existed) and 3. Pablo's point 4 was completed by following Point 4 below. 

Point 4 came from this askubuntu post [kaymes post](https://askubuntu.com/a/1098851)


**See also::** 

### Links to this note:
```query
"[[Fix if link to Zoter doesnt work in Ubuntu (POP OS)]]"
```

