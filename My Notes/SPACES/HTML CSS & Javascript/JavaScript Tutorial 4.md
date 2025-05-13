**up::** [[WEB DESIGN MOC]]
**index::** [[+Index for Personal]]

**tags::** #javascript #variables 
# JavaScript Tutorial 4

**Created:**  11 April 2024 at  10:58 hours.
___
**Previous::** [[JavaScript Tutorial 3]]
**Next::** [[JavaScript Tutorial 5]]
## Variables

1. *Declare* a variable using the `let` command - there are other ways but `let` is best practice for JS
```javascript
let varName;
console.log(varName);
```
2. If this is saved then the HTML file is opened in the Live Server (see [[JavaScript Tutorial 1]]) the variable will show in the Console as undefined ... ![[Pasted image 20240411111718.png|500]]
3. To *initialise* (set the value of) a variable use the **=** notation eg. for setting *varName* to have a value of the string *'Alex'* do this ...
   ```javascript
let varName = 'Alex';
console.log(varName);
```
	**Note**:
	 *'Single quotes'* are best practice for strings though *"double quotes"* work also.
4. Other rules:
	- Variable names cannot be a reserved keyword (let, if, etc) - the editor will warn you!
	- Variable names should be meaningful (not a or b or x etc)
	- Variables cannot start with a number
	- Variables can't contain spaces / hyphen ( eg. **first-name** doesn't work use **firstName**)
	- Variables are case sensitive
5. Variables can optionally be initialised - best practice is one variable declaration per line
-  eg. `let firstName= 'Alex', lastname= 'Delaforce';` will work but this is better ...
  ```javascript
  let firstName = 'Alex';
  let lastName = 'Delaforce;'
``` 


___
**Previous::** [[JavaScript Tutorial 3]]
**Next::** [[JavaScript Tutorial 5]]
**See also::** 

### Links to this note:
```query
"[[JavaScript Tutorial 4]]"
```

