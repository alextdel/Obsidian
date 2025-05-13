**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #elementor #font #default_fonts

# Elementor Font Sizes

**Created:**  15 April 2023 at  14:32 hours.

___
## Controlling Font Sizes in an Elementor Site:
Often the Headings such as H1, H2 are not directly associated with the sizing that is required. H1 may be needed for a particular piece of text and therefore be picked by Google for SEO purposes but may be smaller than other headings. Here are some notes and videos ...

1. Why you don't need to set H1 to H6 sizes directly
   See here for an explanation of the reason why you don't need to set H1 as necessarily the biggest font - [LivingWithPixels - How to Perfectly Set Up Typography & Fonts in Elementor - YouTube](https://www.youtube.com/watch?v=55UkDGfZOp0)

2. A font size chart - from LivingWithPixels
   See here for a font size chart of suggested sizes that includes using the clamp function rather than setting each of the responsive breakpoints ([Font sizes - Living With Pixels](https://livingwithpixels.com/resources/font-sizes/)
	From the video above 
	![[FontSizeSpreadsheet1.png]]

3. Clamp calculator
   Link to the clamp calculator referred to by for a way of scaling fonts - [Font-size clamp() generator](https://clamp.font-size.app/)

4. Setting up font sizes using Global Font settings
   See here for another way of doing the same thing - this one is actually easier to understand - [(77) The Best Way to Setup Elementor Typography - YouTube](https://www.youtube.com/watch?v=GXQ-04_iSNc)
	![[FontSizesSetElementor.png]]

### Using a JSON template file

A handy file that can be used as a site setting template is provided [here](https://drive.google.com/file/d/1Yzokw3FGvGhLtNcj3YN7eJp5cJqInw-b/view?usp=share_link) 
This is a local copy ![[Site Assets Template.json]]
To use this json, make a new page, change setting for the page to 'Canvas' so that heading and footer are not included, insert template, choose my templates, upload and insert the JSON file.
Instructions are included at the end of the video linked here ... YouTube video for the technique from Lead Nerds - [click here](https://youtu.be/7ClcCNfFYOE) 

#### Conclusion:
1. Set up a range of sizes under global fonts from XXL to XS, Label (), Text
eg.
![[GlobalFontPanel.png]]
2. Associate each size set above with the Headings
eg.
![[TypographyHeadings.png]]
3. Use the Heading style as per needed for SEO and basic differentiation
4. Use the Global Fonts to alter sizes for a particular element
5. When setting the fonts - use the responsive breakover sizes or use the clamp calculation - see link above


**See also::** 

### Links to this note:
```query
"[[Elementor Font Sizes]]"
```

