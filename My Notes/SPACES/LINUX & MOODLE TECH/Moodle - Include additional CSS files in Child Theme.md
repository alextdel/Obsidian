**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #css #moodle #child-theme #styles 
# Moodle - Include additional CSS files in Child Theme

**Created:**  21 June 2024 at  09:49 hours.
___
## Including additional CSS files in Child themes Using relative paths:

To make the child theme css style system more modular create separate CSS files for each logical section (e.g., *hero.css*, *header-navigation.css*) and for each purpose (eg,. *Navigation menu styling fixes*, *Dashboard panel image sizes* etc.).

In the `pre.css` or `post.css` file, use the *@import* directive followed by the relative path to the desired CSS file.

For example, to import `hero.css` in the `pre.css` file :


```
/* pre.css */
@import url("hero.css");

/* Your other pre.css styles */
```

Use code [with caution.](/faq#coding)


**See also::** [[Moodle child theme - using git]], [[Moodle - include CSS files using $THEME->sheets variable]] 

### Links to this note:
```query
"[[Moodle - Include additional css files in Child Theme]]"
```

