**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #moodle #child-theme #git #css 
# Moodle child theme - using git

**Created:**  21 June 2024 at  09:18 hours.
___
## Step-by-Step Child Theme Guide using Git

#### Step 1: Setup Your Development Environment

1. **Ensure you have access to your Moodle installation**: This could be a local installation or on a web server.
2. **Navigate to the themes directory**: This is usually located at `yourmoodlesite/theme`.

#### Step 2: Create the Child Theme Directory and Initialize Git

1. **Create a new directory** in the `theme` folder called `tdlk_lrn_remui_child`.

   ```shell
   mkdir yourmoodlesite/theme/tdlk_lrn_remui_child
   cd yourmoodlesite/theme/tdlk_lrn_remui_child
   ```

2. **Initialize a new Git repository** in this directory.

   ```shell
   git init
   ```

#### Step 3: Create Essential Files for the Child Theme

1. **Create the `config.php` file** in the `tdlk_lrn_remui_child` directory.

   ```php
   <?php
   // This file is part of Moodle - http://moodle.org/
   //
   // Moodle is free software: you can redistribute it and/or modify
   // it under the terms of the GNU General Public License as published by
   // the Free Software Foundation, either version 3 of the License, or
   // (at your option) any later version.
   //
   // Moodle is distributed in the hope that it will be useful,
   // but WITHOUT ANY WARRANTY; without even the implied warranty of
   // MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   // GNU General Public License for more details.
   //
   // You should have received a copy of the GNU General Public License
   // along with Moodle.  If not, see <http://www.gnu.org/licenses/>.

   defined('MOODLE_INTERNAL') || die();

   $plugin->component = 'theme_tdlk_lrn_remui_child';
   $plugin->dependencies = array(
       'theme_remui' => '2021051700' // Adjust the version to match your RemUI theme version.
   );

   $THEME->name = 'tdlk_lrn_remui_child';
   $THEME->parents = array('remui');
   $THEME->sheets = array('pre', 'post'); // Add pre.css and post.css
   $THEME->editor_sheets = array();
   $THEME->scss = function($theme) {
       return theme_tdlk_lrn_remui_child_get_main_scss_content($theme);
   };
   $THEME->supportscssoptimisation = false;
   $THEME->usefallback = true;
   $THEME->scss_file = 'styles';
   $THEME->prescsscallback = 'theme_tdlk_lrn_remui_child_get_pre_scss';
   $THEME->extrascsscallback = 'theme_tdlk_lrn_remui_child_get_extra_scss';
   $THEME->rendererfactory = 'theme_overridden_renderer_factory';
   $THEME->requiredblocks = '';

   function theme_tdlk_lrn_remui_child_get_main_scss_content($theme) {
       return '';
   }

   function theme_tdlk_lrn_remui_child_get_pre_scss($theme) {
       return '';
   }

   function theme_tdlk_lrn_remui_child_get_extra_scss($theme) {
       return '';
   }
   ```

2. **Create the `version.php` file** in the `tdlk_lrn_remui_child` directory.

   ```php
   <?php
   defined('MOODLE_INTERNAL') || die();

   $plugin->version   = 2024062100;        // The current plugin version (Date: YYYYMMDDXX).
   $plugin->requires  = 2021051700;        // Requires this Moodle version.
   $plugin->component = 'theme_tdlk_lrn_remui_child'; // Full name of the plugin (used for diagnostics).
   $plugin->dependencies = array(
       'theme_remui' => '2021051700' // This should match the version of RemUI theme you are using.
   );
   ```

3. **Create the `style` directory** in the `tdlk_lrn_remui_child` directory.

   ```shell
   mkdir yourmoodlesite/theme/tdlk_lrn_remui_child/style
   ```

4. **Create `pre.css` and `post.css` files** in the `style` directory.

   ```css
   /* pre.css */
   /* Add your custom CSS that needs to be loaded before the main CSS */
   ```

   ```css
   /* post.css */
   /* Add your custom CSS that needs to be loaded after the main CSS */
   ```

#### Step 4: Add Theme Language Strings

1. **Create the `lang` directory** and the `en` subdirectory in the `tdlk_lrn_remui_child` directory.

   ```shell
   mkdir -p yourmoodlesite/theme/tdlk_lrn_remui_child/lang/en
   ```

2. **Create the `theme_tdlk_lrn_remui_child.php` file** in the `lang/en` directory.

   ```php
   <?php

   // Every file should have GPL and copyright in the header - we skip it in tutorials but you should not skip it for real.

   // This line protects the file from being accessed by a URL directly.
   defined('MOODLE_INTERNAL') || die();

   // The name of the second tab in the theme settings.
   $string['advancedsettings'] = 'Advanced settings';

   // The brand colour setting.
   $string['brandcolor'] = 'Brand colour';

   // The brand colour setting description.
   $string['brandcolor_desc'] = 'The accent colour.';

   // A description shown in the admin theme selector.
   $string['choosereadme'] = 'TDLK LRN RemUI Child is a child theme of the Edwiser RemUI theme. It allows custom CSS to be added before and after the main CSS of the RemUI theme.';

   // Name of the settings pages.
   $string['configtitle'] = 'TDLK LRN RemUI Child settings';

   // Name of the first settings tab.
   $string['generalsettings'] = 'General settings';

   // The name of our plugin.
   $string['pluginname'] = 'TDLK LRN RemUI Child';

   // Preset files setting.
   $string['presetfiles'] = 'Additional theme preset files';

   // Preset files help text.
   $string['presetfiles_desc'] = 'Preset files can be used to dramatically alter the appearance of the theme. See <a href=https://docs.moodle.org/dev/Boost_Presets>Boost presets</a> for information on creating and sharing your own

 preset files, and see the <a href=http://moodle.net/boost>Presets repository</a> for presets that others have shared.';

   // Preset setting.
   $string['preset'] = 'Theme preset';

   // Preset help text.
   $string['preset_desc'] = 'Pick a preset to broadly change the look of the theme.';

   // Raw SCSS setting.
   $string['rawscss'] = 'Raw SCSS';

   // Raw SCSS setting help text.
   $string['rawscss_desc'] = 'Use this field to provide SCSS or CSS code which will be injected at the end of the style sheet.';

   // Raw initial SCSS setting.
   $string['rawscsspre'] = 'Raw initial SCSS';

   // Raw initial SCSS setting help text.
   $string['rawscsspre_desc'] = 'In this field you can provide initialising SCSS code, it will be injected before everything else. Most of the time you will use this setting to define variables.';

   // We need to include a lang string for each block region.
   $string['region-side-pre'] = 'Right';
   ```

#### Step 5: Commit and Push to a Remote Repository

1. **Add all files to the repository** and commit.

   ```shell
   git add .
   git commit -m "Initial commit for TDLK LRN RemUI Child theme"
   ```

2. **Create a repository on GitHub or any other Git hosting service**.

3. **Add the remote repository** to your local repository and push the changes.

   ```shell
   git remote add origin https://github.com/yourusername/tdlk_lrn_remui_child.git
   git push -u origin master
   ```

#### Step 6: Install and Activate the Child Theme

1. **Navigate to your Moodle site**: Go to Site administration > Notifications. Moodle will detect the new theme and prompt you to upgrade the database. Follow the prompts to complete the installation.
2. **Activate the child theme**: Go to Site administration > Appearance > Themes > Theme selector, and select `TDLK LRN RemUI Child` as your current theme.

#### Step 7: Verify and Customize

1. **Clear the cache**: Navigate to Site administration > Development > Purge all caches.
2. **Verify the child theme**: Ensure your custom CSS files (`pre.css` and `post.css`) are being loaded correctly before and after the main CSS.
3. **Customize further**: You can now add custom CSS rules to `pre.css` and `post.css`, and make additional customizations as needed.

### Additional Tips

- **Use Developer Tools**: Use your browser's developer tools to inspect elements and verify that your CSS rules are being applied correctly.
- **Backup**: Always backup your Moodle installation before making significant changes.

By including these additional language strings, your child theme will have a more complete set of options and descriptions, making it easier to manage and customize within the Moodle administration interface.


**See also::** [[Moodle - Include additional CSS files in Child Theme]]

### Links to this note:
```query
"[[Moodle child theme - using git]]"
```

