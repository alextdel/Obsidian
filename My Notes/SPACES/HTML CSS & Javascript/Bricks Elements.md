**up::** [[WP & WP BUILDERS MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #css #bricks #webdesign #sections #containers #blocks #divs

# Bricks Elements

**Created:**  06 June 2023 at  17:05 hours.

___
### Sections, Containers, Blocks and Div

#### Section
- Good for symantic layout
- Everything in a section is related - should add to the logic of the page.
- Sections usually come with a container
	- A section can  contain many containers
- ***Do Not*** add content directly in a section always add a container 

#### Divs
- All other elements are based on *div*
- A container element is a predefined *div*
*Divs* have no predefined width - in a container a *div* shows as a square, outside a *section* a *div* in **bricks** will look like it covers the entire width (but has no width set). The *div* will take the size of its contents.

#### Container
- contains the website's content within a preset width - eg. default 1100px

#### Block
- by default is *display: flex* and *100% width*
- usually don't put in a Section directly, put in a *Container*

Blocks can be used to create columns 
	- a *Div* is a possible alternative but Block is better as:
		- *Block* will have 100% width but *Div* has  no width by default
		- *Block* is *display: flex;* by default.
		- *Div* is *display: block;* by default.

> **Column:**
> A column is a type of block.
> When a column is added to a *Container* the settings are preset to:
> 	- *direction: horizontal;*
> 	- *display:  flex;*
> *At the front view, the column is rendered as a block element*



**See also::** 

### Links to this note:
```query
"[[Bricks Elements]]"
```

