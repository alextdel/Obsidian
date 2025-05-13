**up::** [[WP & WP BUILDERS MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #website #WordPress #paragraph_spacing #ordered_lists #unordered_lists #customCSS 

# Wordpress ul and ol lists - Fix paragraph spacing

**Created:**  23 February 2023 at  21:47 hours.

___
### Note:
In the case of uneven or incorrect spacing before and after ordered (ol) and unordered (ul) lists in WordPress (including when using Elementor), the following can be added to the Wordpress > Appearance >Customize > Additional CSS item in the WordPress (not Elementor) dashboard.

```
.elementor-widget-text-editor ul, .elementor-widget-theme-post-content ul, .elementor-widget text-editor ol, .elementor-widget-theme-post-content ul
{
margin-bottom:1.0em;
margin-top:1.0em;
}
```

The CSS will apply to only *ol* and *ul* tags in the listed widgets, the avoids problems when the *ol* and *ul* tags may be used for other reasons, such as CSS menus etc.

**See also::** This [web page](https://geekonheels.com/tutorial/so-you-need-some-space-under-your-bulleted-lists/)

### Links to this note:
```query
"[[Wordpress ul and ol lists - Fix paragraph spacing]]"
```

