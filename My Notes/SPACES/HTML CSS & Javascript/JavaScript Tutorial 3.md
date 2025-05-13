**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]

**tags::** #webdesign #javascript #node 
# JavaScript Tutorial 3

**Created:**  11 April 2024 at  09:51 hours.
___
**Previous::** [[JavaScript Tutorial 2]]
**Next::** [[JavaScript Tutorial 4]]
## JavaScript in Node:

This tutorial is from [this section](https://www.youtube.com/watch?v=TlB_eWDSMt4&t=629s) of [Node.js Tutorial for Beginners: Learn Node in 1 Hour](https://www.youtube.com/watch?v=TlB_eWDSMt4)
This shows the setup of Node and a first Node application in JS. It also demonstrates that Node doesn't include Window objects that are usually provided by browsers, hence the error shown at the end 

1. Make a new folder for our JS app - eg. `mkdir first-app` ... ![[Pasted image 20240411102208.png|300]]
2. in VS Code create a new file called app.js ... ![[Pasted image 20240411102308.png]]
3. Add code to app.js 
   ```javascript
   function sayHello(name) {
      console.log('Hello ' + name);
   }
   sayHello('Alex');
```

4. save *Ctrl+S*
5. in terminal run `node app.js` ... ![[Pasted image 20240411102104.png|400]]
Next
6. comment out the `sayHello('Alex');` line and replace with `console.log(Window);`  ... ![[Pasted image 20240411102554.png|300]]
7. Save and run - this will show an exception because node doesn't include *window* or *document* objects ... ![[Pasted image 20240411102747.png|500]]

___
**Previous::** [[JavaScript Tutorial 2]]
**Next::** [[JavaScript Tutorial 4]]

**See also::** 
### Links to this note:
```query
"[[JavaScript Tutorial 3]]"
```

