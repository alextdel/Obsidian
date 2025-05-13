**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #css #Moodle #styles 
# Moodle - include CSS files using $THEME->sheets variable

**Created:**  21 June 2024 at  09:56 hours.
___
### How to use the `$THEME->sheets` variable:

If CSS files are in the same directory (eg. Child theme styles directory) then [[Moodle - Include additional CSS files in Child Theme]] is an easier method to use.
The method shown here is recommended if CSS files are located in a different directory. It leverages Moodle's theme configuration to include additional stylesheets.

Here's how it works:

- Add additional entries to the `$THEME->sheets` array in your `config.php` file. Each entry should be the filename of your custom CSS file (without the `.css` extension).
- In your `pre.css` or `post.css` file, you don't need to use any `@import` statements. The theme will automatically load the additional stylesheets in the order they appear in the `$THEME->sheets` array.

For example, if your custom CSS files are located in a subdirectory called `styles`:

- In your `config.php` file:

PHP

```
$THEME->sheets = array('pre', 'post', 'styles/hero', 'styles/header-navigation');
```

Use code [with caution.](/faq#coding){{content}}


**See also::** [[Moodle child theme - using git]], [[Moodle - Include additional CSS files in Child Theme]]

### Links to this note:
```query
"[[Moodle - include additional CSS files using $THEME->sheets variable]]"
```

