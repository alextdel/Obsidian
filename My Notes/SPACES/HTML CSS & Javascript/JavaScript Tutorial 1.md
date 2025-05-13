**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]

**tags::** #webdesign #javascript
# JavaScript Tutorial 1

**Created:**  11 April 2024 at  09:15 hours.
___
**Previous::** [[JavaScript - setup JS and Node environment]]
**Next::** [[JavaScript Tutorial 2]] 

## First Script - Using the Browser Console

This follows on from the setup note below - based on this [YouTube tutorial](https://www.youtube.com/watch?v=W6NZfCO5SIk&t=354)

1. Add the script element either in the `<head>` section or the `<body>` section
	- The best practice is at the end of the `<body>` section after all the other elements
		- Browser parses top to bottom so placing in `<head>` slows down rendering of webpage.
		- JS usually 'talks' to the elements on the webpage, so its more effective to allow the HTML to be read first.
	- There are exceptions including when 3rd party scripts require they be placed in the `<head>` section.
2. Place the cursor at the insertion point, type script, press tab to give this ... ![[Pasted image 20240411092247.png|200]]
3. Type the first script to talk to the JS console
   ```HTML
<body>
<h1>Hello world</h1>
<script>
// Comment describing the why and how of the script
// Save this file then 'Open with Live Server' from VS Code Explorer
console.log('Hello world');
</script>
</body>
```
	- Save and right click on the Live Server page > select *Inspect* > open the Console
		- Alternatively Ctrl+Shft+K (on Linux Firefox)
This should show Hello World in the console.

**Previous::** [[JavaScript - setup JS and Node environment]]
**Next::** [[JavaScript Tutorial 2]] 

**See also::** [[JavaScript - setup JS and Node environment]]

### Links to this note:
```query
"[[JavaScript Tutorial 1]]"
```

