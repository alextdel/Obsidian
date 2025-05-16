**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]

**tags::** #css #scss #webdesign 

**Created:**  01 May 2025 at  20:44 hours.
___
# SCSS vs Raw CSS
SCSS (Sassy CSS) is a preprocessor scripting language that's interpreted or compiled into standard CSS. Here's how SCSS differs from raw CSS:
## Key Differences
### 1. Nesting Capabilities
**SCSS:**

```scss
nav {
  background-color: #333;
  
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
    
    li {
      display: inline-block;
      
      a {
        color: white;
        text-decoration: none;
        
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }
}
```

**Equivalent CSS:**

```css
nav {
  background-color: #333;
}
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav ul li {
  display: inline-block;
}
nav ul li a {
  color: white;
  text-decoration: none;
}
nav ul li a:hover {
  text-decoration: underline;
}
```

### 2. Variables

**SCSS:**

```scss
$primary-color: #3498db;
$secondary-color: #2ecc71;
$font-stack: 'Helvetica', sans-serif;

body {
  font-family: $font-stack;
  color: #333;
}

.button {
  background-color: $primary-color;
  
  &.success {
    background-color: $secondary-color;
  }
}
```

**Equivalent CSS:**

```css
body {
  font-family: 'Helvetica', sans-serif;
  color: #333;
}

.button {
  background-color: #3498db;
}

.button.success {
  background-color: #2ecc71;
}
```

### 3. Mixins (Reusable Code Blocks)

**SCSS:**

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

.box {
  @include border-radius(10px);
}

.circle {
  @include border-radius(50%);
}
```

**Equivalent CSS:**

```css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;
}

.circle {
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;
}
```

### 4. Operations and Functions

**SCSS:**

```scss
$container-width: 100%;
$column-count: 4;
$margin: 10px;

.column {
  width: ($container-width / $column-count) - (2 * $margin);
  margin: 0 $margin;
}
```

**Equivalent CSS:**

```css
.column {
  width: calc(25% - 20px);
  margin: 0 10px;
}
```

### 5. Partials and Imports

**SCSS:**

```scss
// _variables.scss
$primary-color: #3498db;

// _navigation.scss
nav {
  background-color: $primary-color;
}

// main.scss
@import 'variables';
@import 'navigation';

body {
  font-family: sans-serif;
}
```

In CSS, all imports create additional HTTP requests, but SCSS imports are combined during compilation.

### 6. Inheritance

**SCSS:**

```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}
```

**Equivalent CSS:**

```css
.success, .error {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}
```

## Practical Advantages of SCSS

1. **Maintainability**: Easier to maintain and update large stylesheets
2. **Organisation**: Better code organisation with nesting and partials
3. **Efficiency**: Less repetition through variables and mixins
4. **Scalability**: More scalable for large projects
5. **Modularity**: Allows breaking styles into smaller, manageable files
6. **Logic**: Supports control directives like if/else statements and loops

## Using SCSS in Grav Themes

For Grav themes like Oxygen that use SCSS:

1. The source files are written in SCSS (.scss files)
2. A build process (typically using Gulp, Webpack, or npm scripts) compiles these to CSS
3. The compiled CSS is what's actually used by the browser
4. When creating a child theme, you can either modify the SCSS (requiring compilation) or add overrides directly in CSS

If you're new to SCSS, starting with direct CSS overrides in your child theme is simpler, but learning SCSS would be beneficial for more comprehensive theme customisations.


**See also::** 

### Links to this note:
```query
"[[SCSS compared to Raw CSS]]"
```

