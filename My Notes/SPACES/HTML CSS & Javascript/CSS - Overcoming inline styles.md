**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #css #inlinestyles #important'  

# CSS - Overcoming inline styles

**Created:**  16 November 2022 at  14:49 hours.

___
### Note:
If the design of an element is controlled directly by an 'inline' style, normal custom CSS will not take the place of the inline style.
The only way to do this is to indicate **'!important'**
for example, if this is the element and styling
```
<div style="background: red;">
   The inline styles for this div should make it red.
</div>
```

this can be fought by using the following - from [Override Inline Styles with CSS | CSS-Tricks - CSS-Tricks](https://css-tricks.com/override-inline-styles-with-css/)
```
div[style] { background: yellow !important; }
```

---

In https://learn.tiddalik.com.au the custom styling entry here is used to resize the course card images and to overrulle the inline style 
```
/* resizes the category course card images and sets TDLK background color*/
/*======================*/
.courseimage  {
  background-size: contain !important;
  background-repeat: no-repeat;
background-color: #045957 !important;
   
}
```


**See also::** 

### Links to this note:
```query
"[[CSS - Overcoming inline styles]]"
```

