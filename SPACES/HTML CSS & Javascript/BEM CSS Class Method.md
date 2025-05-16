**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #BEM #css #classes #webdesign 

# BEM CSS Class Method

**Created:**  09 June 2023 at  09:13 hours.

___
### Note:
From [CSS TRICKS BEM 101](https://css-tricks.com/bem-101/) article
The **Block, Element, Modifier** methodology (commonly referred to as [BEM](https://en.bem.info/methodology/quick-start/)) is a popular _naming convention_ for classes in HTML and CSS.

Here’s an example of what a CSS developer writing in the BEM style might write:

```css
/* Block component */
.btn {}

/* Element that depends upon the block */ 
.btn__price {}

/* Modifier that changes the style of the block */
.btn--orange {} 
.btn--big {}
```

A **block** is a top-level abstraction of a new component, for example a button: `.btn { }`. This block should be thought of as a parent. Child items, or **elements**, can be placed inside and these are denoted by two underscores following the name of the block like `.btn__price { }`. Finally, **modifiers** can manipulate the block so that we can theme or style that particular component without inflicting changes on a completely unrelated module. This is done by appending two hyphens to the name of the block just like `btn--orange`.

The markup might then look like this:

```html
<a class="btn btn--big btn--orange" href="https://css-tricks.com">
  <span class="btn__price">$9.99</span>
  <span class="btn__text">Subscribe</span>
</a>
```


**See also::** 

### Links to this note:
```query
"[[BEM CSS Class Method]]"
```

