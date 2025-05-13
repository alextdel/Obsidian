**up::** [[WP & WP BUILDERS MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #elementor #WordPress #http #https

# Wordpress Elementor Tips

**Created:**  24 October 2022 at  21:31 hours.

___
### Note:
The following contains any tips and procedures found related to Elementor and using this with WordPress
1. Template Editor images look correct but live site images show only original size
	- Problem found to be that Bitnami WordPress is only using http and this is hardcoded in the /opt/bitnami/wordpress/wp-config.php file (if the http settings show greyed out in the Wp general settings page)
	- Go to wp-config.php and alter these lines to show https (they will be on http)
	   ![[WP_configPHP file.png]]
	   - instructions for changing url settings in WordPress shown here - https://www.wpbeginner.com/wp-tutorials/how-to-change-your-wordpress-site-urls-step-by-step/


**See also::** 

### Links to this note:
```query
"[[Wordpress Elementor Tips]]"
```

