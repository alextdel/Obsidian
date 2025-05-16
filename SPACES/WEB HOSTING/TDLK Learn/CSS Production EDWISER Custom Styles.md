**up::** [[TIDDALIK Web MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #css #Edwiser #customCSS 

**Created:**  28 August 2022 at  10:49 hours.

___
## Custom CSS
This custom CSS contains comments to explain the custom settings.
section controls the spacing around the footer elements
```
/*controls the footer spacing to make it more compact*/
#page-footer div.footer-content-debugging.footer-dark div {
padding-top: 0.1rem;
padding-right: 1.0rem;
padding-bottom: 0.1rem;
padding-left: 1.0rem; 
}

/*controls the header menu active item underline color*/
.moremenu .nav-link.active {
    border-bottom-color: rgb(4, 89, 87, 0.8);
}

/*controls the hr line in the footer and its color and margin - makes footer more compact*/
#page-footer > div.footer-content-debugging.footer-dark > div > hr{
height: 4px;
background-color: #94c83d;
border: none;
margin: 3px
}

.navbar-options{
font-size: 14px;
text-transform: uppercase;
}
/*Following CSS is for front page image and text*/
.flexbox-container { 
  display: flex;
  flex-direction: row;
  justify-content: center;  
  margin: 0 0 0 30px;
  }

#leftimage {
   max-width: 400px;
    
}
#righttext {
     width: 400px;
    background-color: #94c83d;
    padding: 0.8em;
}
#righttext p {
  font-size: 1em;
  color: black;
  font-family: raleway;
  margin: 0px;
  padding: 0 0 0.8em 0;
}

@media only screen and (max-width: 802px)
{

.flexbox-container{
flex-direction: column;
margin-left: 120px;}

#leftimage {
width: 400px;}

#righttext{
width: 400px;}

}

@media only screen and (max-width: 480px)
{

.flexbox-container{
flex-direction: column;
margin-left: 20px;}

#leftimage {
width: 300px;}

#righttext{
max-width: 300px;
padding: 0.3em;}

#righttext p {
padding: 0 0 0.2em 0;}

}

/*=====================*/
/* resizes the category course card images and sets TDLK background color*/
/*======================*/
.courseimage  {
  background-size: contain !important;
  background-repeat: no-repeat;
background-color: #045957 !important;
   
}
/*=====================*/
/* resizes the available course card images and sets TDLK background color*/
/*======================*/
.rounded-top  {
  background-size: contain !important;
  background-repeat: no-repeat;
background-color: #045957 !important;
   
}

/*=====================*/
/* sets the popup footer (the question mark popup) so that the background is dark green and the text is light yellow*/
/*======================*/
.bg-primary{
background-color: #045957  !important;
}
.popover-body{
color: #ffffcc;
}
```

**See  also::** [[📙CSS Staging ... EDWISER Custom Styles]]