**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Linux #shell_script #coding #bash #sh #programming

# Linux Shell Scripts

**Created:**  03 April 2023 at  11:04 hours.

___
### Note:
1. Detect if a device is connected
```sh
#!/bin/bash
if lsusb | grep -q "056a:": then
    echo "Wacom Intuos tablet detected"
else
    echo "Wacom Intuos tablet not detected"
fi
```

The `lsusb` command lists all the connected USB devices, and the output is piped to the `grep` command to search for the Wacom device ID, which is "056a:".
	The `-q` option tells `grep` to be quiet and only return an exit code, without printing any output. 
The `if` statement checks the exit code of the `grep` command, and if it's zero (which means the Wacom device is found), the script outputs "Wacom Intuos tablet detected". If the Wacom device is not found, the script outputs "Wacom Intuos tablet not detected".

Note that the device ID ("056a:") may vary depending on the exact model of your Wacom Intuos tablet. You can use the `lsusb` command without `grep` to see the list of USB devices and their IDs, and find the correct ID for your device.

2. Creating a function in a bash shell script:
```sh
#!/bin/bash

# define the function
my_function() {
    # your code goes here
    echo "Hello, world!"
}

# call the function
my_function
```

4. Passing arguments to a function:
Pass arguments to the function by specifying them inside the parentheses, like `my_function argument1 argument2`. Inside the function, you can access the arguments using the `$1`, `$2`, `$3`, etc. variables
```sh
#!/bin/bash

# define the function
greet() {
    name=$1
    echo "Hello, $name!"
}

# call the function with an argument
greet "Alice"
```
6. How to pass two parameters to a shell script function:
```sh
#!/bin/bash

# define the function
sum() {
    num1=$1
    num2=$2
    total=$(($num1 + $num2))
    echo "The sum of $num1 and $num2 is $total"
}

# call the function with two arguments
sum 5 7
```
8. How a shell function can return its result to the main code:
```sh
#!/bin/bash

# define the function
get_greeting() {
    name=$1
    echo "Hello, $name!"
}

# call the function and store the result in a variable
greeting=$(get_greeting "Alice")

# print the result
echo $greeting
```
To capture the result of the function in the main code block, we use command substitution, which is done by enclosing the function call inside `$()`. The result of the function call is then stored in the `greeting` variable.

Finally, we print the result by using the `echo` command to output the value of the `greeting` variable. The output of the script will be `"Hello, Alice!"`.

**See also::** 

### Links to this note:
```query
"[[Linux Shell Scripts]]"
```

