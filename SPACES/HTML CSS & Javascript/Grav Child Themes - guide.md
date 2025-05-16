**up::** {enter link to appropriate MOC}
**index::** [[+Index for Personal]]

**tags::** #Grav #child-theme 

**Created:**  02 May 2025 at  16:22 hours.
___
# Creating a Child Theme in Grav CMS: Complete Guide

This document provides a step-by-step procedure for creating a child theme in Grav CMS, specifically using the `quark-open-publishing` theme as an example parent. This approach allows you to customise a theme while maintaining the ability to receive parent theme updates.

## Benefits of Creating a Child Theme
- Seamless parent theme upgrades
- Ability to customise and override specific components
- Control over which dependencies to include
- Proper separation of custom code from parent theme
- Better long-term maintenance

## Step-by-Step Procedure

### 1. Create the Child Theme Directory Structure

First, set up the necessary directories for your child theme:

```bash
mkdir -p user/themes/my-custom-theme
mkdir -p user/themes/my-custom-theme/templates
mkdir -p user/themes/my-custom-theme/css
```

### 2. Create the Child Theme YAML Configuration

Create the theme configuration file. Note that in Grav, this file should be named after your theme folder:

```bash
nano user/themes/my-custom-theme/my-custom-theme.yaml
```

Add the following content to set up theme inheritance:

```yaml
streams:
  schemes:
    theme:
      type: ReadOnlyStream
      prefixes:
        '': 
          - 'user/themes/my-custom-theme'
          - 'user/themes/quark-open-publishing'
```

This configuration tells Grav to look first in your custom theme directory, then fall back to the parent theme if a file isn't found.

### 3. Create the Blueprint File

The blueprint file contains metadata about your theme:

```bash
nano user/themes/my-custom-theme/blueprints.yaml
```

Add the following content, adjusting the details as needed:

```yaml
name: My Custom Theme
version: 1.0.0
description: A child theme of Quark Open Publishing without Git Sync
icon: rebel
author:
  name: Your Name
  email: your.email@example.com
  url: https://yourwebsite.com
homepage: https://github.com/yourname/my-custom-theme
license: MIT

dependencies:
  - { name: grav, version: '>=1.6.0' }
  # Only include plugins you *actually* want
  - archives
  - breadcrumbs
  - external_links
  - feed
  - markdown-notices
  - page-inject
  - pagination
  - simplesearch
  - shortcode-core
  - taxonomylist
  - quark

form:
  validation: loose
  fields:
    tabs:
      type: tabs
      active: 1
      # You can include specific form fields from the parent theme here
      # or leave this section minimal if you primarily want to inherit
```

Note: Grav doesn't use an explicit `inherits` key in theme blueprints. Theme inheritance is handled through the streams configuration in the theme's YAML file.

### 4. Create a Custom Theme Class File

This PHP file extends the parent theme's class:

```bash
nano user/themes/my-custom-theme/my-custom-theme.php
```

Add the following content:

```php
<?php
namespace Grav\Theme;

class MyCustomTheme extends QuarkOpenPublishing
{
    // You can override methods from the parent theme here if needed
}
```

### 5. Set Up Template Inheritance

Create a base template to ensure proper template inheritance:

```bash
nano user/themes/my-custom-theme/templates/partials/base.html.twig
```

With minimal content to start:

```twig
{% extends '@theme/partials/base.html.twig' %}
```

This ensures that your theme inherits templates from the parent theme.

### 6. Activate the Child Theme

You can activate your theme in one of two ways:

#### Option 1: Edit the system.yaml configuration file:

```bash
nano user/config/system.yaml
```

Find the theme setting and change it:

```yaml
pages:
  theme: my-custom-theme
```

#### Option 2: Activate via the Admin plugin:

1. Go to Admin > Configuration > System
2. Find the "Theme" dropdown under the "Pages" section
3. Select your new theme
4. Save the configuration

### 7. Remove/Disable Git-Sync Plugin (Optional)

If you want to remove the git-sync dependency completely:

```bash
rm -rf user/plugins/git-sync
```

Or if you just want to disable it:

```bash
mkdir -p user/config/plugins
echo "enabled: false" > user/config/plugins/git-sync.yaml
```

### 8. Clear Cache

After making all these changes, clear your Grav cache:

```bash
bin/grav clear-cache
```

### 9. Add Custom CSS (Optional)

To add custom styling, create a CSS file:

```bash
nano user/themes/my-custom-theme/css/custom.css
```

Add your custom styles to this file. You may need to include this file in your templates depending on the parent theme's structure.

## Overriding Specific Components

### Templates

To override a template, copy it from the parent theme to your child theme with the same path. For example:

```bash
cp user/themes/quark-open-publishing/templates/partials/navigation.html.twig user/themes/my-custom-theme/templates/partials/navigation.html.twig
```

Then edit the copied template as needed.

### CSS/JavaScript

To override CSS or JavaScript, create your own files in the appropriate directories and include them in your templates or use the theme's asset management capabilities.

## Troubleshooting

If your child theme doesn't appear to be working correctly:

1. Ensure your theme folder name matches the YAML and PHP filenames
2. Verify the streams configuration is set up correctly
3. Make sure the parent theme is installed
4. Clear the cache after making changes
5. Check Grav's debug log for any errors

## Best Practices

- Only override the specific components you need to change
- Keep your customisations organised and documented
- Consider version control for your child theme
- Update your parent theme regularly to get security updates and bug fixes
- Test thoroughly after parent theme updates

---

This guide follows Grav's best practices for theme inheritance and provides a maintainable, long-term solution for theme customisation.

**See also::** 

### Links to this note:
```query
"[[Grav Child Themes - guide]]"
```

