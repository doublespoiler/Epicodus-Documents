# JAVASCRIPT CHEATSHEET

- [[#Data Types|Data Types]]
	- [[#Data Types#Primitives|Primitives]]
	- [[#Data Types#Numbers|Numbers]]
	- [[#Data Types#Strings|Strings]]
	- [[#Data Types#Objects|Objects]]
- [[#Declarations|Declarations]]
- [[#Operators|Operators]]
- [[#Functions|Functions]]
	- [[#Functions#Declaring a function|Declaring a function]]
	- [[#Functions#Calling a function|Calling a function]]
	- [[#Functions#Built-in functions|Built-in functions]]
- [[#Methods|Methods]]
	- [[#Methods#Built-in methods|Built-in methods]]
	- [[#Methods#Prototype Methods|Prototype Methods]]
- [[#Arguments|Arguments]]
- [[#Other|Other]]
	- [[#Other#Conventions|Conventions]]
  
## Data Types

### Primitives

Can only reprsent a single type and piece of data

| Name      | Description       | Example                      | Notes                   |
| --------- | ----------------- | ---------------------------- | ----------------------- |
| Number    | Just a number     | `const myNumber=5;`          |                         |
| String    | Text              | `const myString = "Hello.";` | Must be in quotes       |
| Boolean   | true/false        | `const myBool = true;`       |                         |
| Null      | no value yet      | `let myVar = null;`          | We will change it later |
| Undefined | no value          |                              |                         |
| Symbol    | unique primitive  |                              |                         |
| BigInt    | Very large number | 2^52, etc.                   |                         |
|           |                   |                              |                         |

[TOP](#javascript-cheatsheet)

### Numbers

- Expressions return a value (math)
- NaN - Not a number (but it's technically a number in JS)
- Infinity - Dividing a number by 0 (also technically a number in JS)*
- int - interger
- float - has decimals

[TOP](#javascript-cheatsheet)

### Strings

| Name       | Description   | Example                                    | Notes                                                         |
| ---------- | ------------- | ------------------------------------------ | ------------------------------------------------------------- |
| `\`        | escape        | `"Quoth the raven, \"Nevermore.\"";`       | Tells JS the next character is just a character in the string |
| `'"text"'` | single quotes | `'"programming is fun!", she exclaimed.';` | Allows you to use "" for quotes inside                        |

[TOP](#javascript-cheatsheet)

### Objects

Containers for related data, and its functionality
Ex: Animal object, contains data about height, color, eating, meowing, etc.
Ex: Computer object, contains data about GPU, CPU, playing games, browsing web, etc.
Object methods do something
Object properties are just information about the object
Object methods are also a property of the object.

```js
let cat = {
  age: 13,
  likesTunaFish: true,
  likesComputerProgramming: false,
  talk: function() { //This creates a method!
    return "meow!";
  } //call with cat.talk();
}
```



```js
let nameOfObjectType = {
  propertyName: value,
  secondProperty: anotherValue,
  thirdProperty: thirdValue
}
```

Accessing Object Properties

```js
object.propertyNameInCamel;
parentObject.childObject.targetProperty;
```


## HTML DOM
![[tree.png]]

Accessing DOM
```js
window.document;
```

Selecting HTML elements
```html
<h1 id="specialHeader">Best Chocolae Chip Cookies!</h1>
```
```js
window.document.querySelector("h1"); 
```

Selecting by class
```html
<ol class="ol.style">
	<li></li>
	<li></li>
	<li></li>
</ol>
```
```js
window.document.querySelector("ol.ol-style"); 
```

Selecting children
```html
<ol class="ol.style">
	<li></li>
	<li></li>
	<li></li>
</ol>
```
```js
window.document.querySelector("ol>li"); //only selects the li
```

Selecting by ID
```html
<h1 id="specialHeader">Best Chocolae Chip Cookies!</h1>
```
```js
window.document.getElementByID("specialHeader");
```
```js
window.document.getElementByID("h1#specialHeader");
```

HTML ELEMENT === DOM OBJECT
DOM objects are representations of html elements in the DOM (browser window)

[TOP](#javascript-cheatsheet)

## Declarations

| code  | description | example                 | notes                                                                                   |
| ----- | ----------- | ----------------------- | --------------------------------------------------------------------------------------- |
| var   | variable    | `var myNumber = 0;`     | Old, don't use                                                                          |
| let   | variable    | `let myNumber = 0;`     | Use instead of var, indicates the variable will change, will not let you double declare |
| const | constant    | `const myConstant = 0;` | cannot change, value must be declared, will not let you double declare                  |

[TOP](#javascript-cheatsheet)

## Operators

| symbol           | name                             | example                                                | notes                                        |                                                                                           |
| ---------------- | -------------------------------- | ------------------------------------------------------ | -------------------------------------------- | ----------------------------------------------------------------------------------------- |
| =                | assignment                       | `const favoriteNumber = 42;`                           | sets variable equal to value                 |                                                                                           |
| +                | concatenation (addition)         | `1 + 3`, `"I love " + "strings."'`                     |                                              |                                                                                           |
| -, * , /         | arithmetic                       | It's just like math                                    |                                              |                                                                                           |
| +=, -=, \*=,  /= | arithmetic assignment            | `myVar += 1'`                                          | does arithmetic and assigns at the same time |                                                                                           |
| <                | comparator less than             | `5 < 10;`                                              | returns boolean                              |                                                                                           |
| <=               | comparator less than equal to    | `5 <= 10;`                                             | returns boolean                              |                                                                                           |
| >                | comparator greater than          | `5 > 10;`                                              | returns boolean                              |                                                                                           |
| >=               | comparator greater than equal to | `5 >= 10;`                                             | returns boolean                              |                                                                                           |
| ===              | strict equality                  | check to see if two operands have the same value       | `myNumber === 5'`                            | returns boolean                                                                           |
| !==              | strict ineequality               | check to see if two operands have the different values | `myNumber !== 5'`                            | returns boolean                                                                           |
| ==               | equality                         | check to see if two operands have the same value       | `myNumber == 5'`                             | attempts to compare operands that are of different data types, returns boolean DO NOT USE |
| !=               | inequality                       | check to see if two operands have different values     | `myNumber != 5'`                             | attempts to compare operands that are of different data types, returns boolean DO NOT USE |
| typeof           | returns the data type            | `typeof myString;`                                     | returns as string                            |                                                                                           |

[TOP](#javascript-cheatsheet)

## Functions 

A bundle of code that performs a set of procedures/operations
They allow us to DO things
Describes actions our code can perform
Functions do not have a *reciever*, unlike methods.
Ex: Turning string "hello" to "HELLO" using a function
Parameter: Placeholder for an argument
Argument: Passed INTO a parameter

[TOP](#javascript-cheatsheet)

### Declaring a function

```js
// This is a function declaration.
function addEmphasis(stringParam) {
  const result = stringParam.toUpperCase().concat("!!!");
  return result;
}
```

```js
function functionNameInCamelCase(parametersSeparated, byCommas) { //curly brackets indicate body
  statement; //statements end with semicolon;
  statement; //We can call
  return; //use return o make the data inside the function available outside of it
} //no semicolon!
```
[TOP](#javascript-cheatsheet)

### Function Expressions 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function#named_function_expression

Storing a function inside a variable
```js
const add = function(number1, number2) {
	return number1 + number2;
}; //NOTE SEMICOLON
// This is known as the "function literal" way of declaring a funcion
```
Use a semicolon at the end, because we are assigning a value to a variable. Notice the function does not have a name.

JS Interpreters (which interpret JS for programs to use) do **HOISTING**, or moving declarations of functions and variables to the top of their scope, before the execution of code.

```js
const result = add(3, 5);
function add(number1, number2) {
   return number1 + number2;
}
result;
```
The result is 8, because the function `add()` is **HOISTED** to the top, even though it is declared after our  `const result` in our code. This ONLY happens with function declarations, NOT expressions (see below, note the `const add = function()`)
```js
const result = add(3, 5);
const add = function(number1, number2) {
   return number1 + number2;
}
result;
```
The function in this code is an expression because it uses `const add =` instead of `function add()`. As a result, it has not been hoisted, and when we call `add()` in the first line, there is no function to call, as it  has not yet been defined.

### Calling a function

```js
addEmphasis("I love my pet rabbit");
```

```js
functionName(functionArgument);
```

[TOP](#javascript-cheatsheet)

### Built-in functions

| code        | description                           | example                       | arguments | notes                      |
| ----------- | ------------------------------------- | ----------------------------- | --------- | -------------------------- |
| console.log | returns argument to console           | `console.log("hello world");` | any       | useful for debugging       |
| parseInt    | attempts to turn string into interger | `parseInt(myString);`         | string    | will turn floats into ints | 
| parseFloat  | attempts to turn string into float    | `parseFloat(myString);`       | string    |                            |

[TOP](#javascript-cheatsheet)

## Methods 

A type of function that **belongs** to a specific data type/object
We **call** a method **on** something (the **reciever**) (including *variables*), asking the method to perform its actions on the data type it belongs to (it can only call that data type)
Can string methods together `"This is a string".concat("!!!", " I like strings!").toUpperCase();` (they go in order) - returns "THIS IS A STRING!!! I LIKE STRINGS!"
Hint: the "." means "called on," this is how you identify methods vs functions!

[TOP](#javascript-cheatsheet)

### Built-in methods 

| code        | description                                                                          | example                              | arguments        | notes                                                                  |
| ----------- | ------------------------------------------------------------------------------------ | ------------------------------------ | ---------------- | ---------------------------------------------------------------------- |
| toUpperCase | returns string in all Uppercase                                                      | `"This is a string.".toUpperCase();` | none             | can be called on ANY string                                            |
| toLowerCase | returns string  in all lowercase                                                     | `"HELLO".toLowerCase();`             | none             | can be called on any string                                            |
| conCat      | returns string with concat argument on the end                                       | `"This is a string".concat("!!!");`  | string to attach | ex: returns "This is a string!!!", accepts multiple arguments          |
| charAt      | returns characer at arg (number)                                                     | `"caterpiller".charAt(5)'`           | number           | first character is 0                                                   |
| toString    | returns as string                                                                    | `numberVar.toString();`              | any              |                                                                        |
| toFixed     | returns number as string with indicated number of decimals                           | `42.222.toFixed(2);`                 | number           | returns 42.22                                                          |
| trim        | trims whitespace from both ends of a string                                          |                                      |                  |                                                                        |
| replace     | returns a new string with some or all matches of a pattern replaced by a replacement |                                      |                  | If the argument is a string, only the FIRST occurence will be replaced |
|             |                                                                                      |                                      |                  |                                                                        |

[TOP](#javascript-cheatsheet)

### Prototype Methods 
Prototype methods refrence built-in methods that belong to a specific data type. It's just a reference to its official name.

```js
dataType.prototype.methodName()
```

```js
String.prototype.conCat()
```

References the conCat method for ONLY STRINGS

[TOP](#javascript-cheatsheet)

## Arguments

Go in parenthesis of function/method

[TOP](#javascript-cheatsheet)

## Scope

Where code is located 
What can access that code
Whether that code can be modified
### Local scope
Variables inside of functions
It is created and destroyed each time the function runs

Wrong:
```js
function sampleFunction() {
  let localString = "This is a local variable";
  window.alert(localString);
  localString = "This is a local variable update!!";
  window.alert(localString);
}

sampleFunction(); 
window.alert(localString); // Uncaught ReferenceError: localString is not defined
```

Right:
```js
function sampleFunction() {
  let localString = "This is a local variable";
  window.alert(localString);
  localString = "This is a local variable update!!";
  window.alert(localString);
  return localString; // new line of code!
}

const globalString = sampleFunction();  // updated code!
window.alert("The value of 'localString' at the global scope: " + globalString); // updated code!
```

You need to reurn in order to access the value of `localString` outside of the function `sampleFunction()`.

### Global Scope

Variables at the "top level" of a .js file
Can be accessed and modified by all code
Be careful about declaring local variables without LET!

```js
let globalString = "This is a global variable"; //outside of function

function sampleFunction() {
  window.alert(globalString);
  globalString = "This is a global variable update!!";
  window.alert(globalString);
}

window.alert(globalString);
sampleFunction();
window.alert(globalString);
```

```js
let bunnyName = "Flopsy";

function hippityHoppity() {
  let bunnyName = "Mopsy";
  window.alert(bunnyName);
  bunnyName = "Cottontail";
}

hippityHoppity();
window.alert(bunnyName);
```

[TOP](#javascript-cheatsheet)

## Other

`myNumber += 5;` increments myNumber by 5
Statements do not reurn variables
`// comment`
`/* inline comment */`

[TOP](#javascript-cheatsheet)

### Conventions

- use `let` or `const` to declare variables
- use lower camelCase in variableNames
- use descriptive names for variables
- use semicolons after statements and expressions
- statements can be made of expressions
- expressions evaluate a value
- statements perform actions
- don't add a semicolon at the end of function delcaration
- business logic - the scripts that DO things 
- interface logic - the scripts that allow the user to interact with the computer

[TOP](#javascript-cheatsheet)

### Scope

### Property Methods
What type of object a variable has
Object.prototype.toString.call(VARNAME);

### Event Handling

event handler properties "listen" for an event on an object that it has been attached to. When he event hapens, the event handler runs our code as a reaction.

```js
target.eventHandler = function() { 
	//function body
};
```

remove an event handler
```js
target.eventHandler = null;
```


| event Handler | descripiton                                 | notes             |
| ------------- | ------------------------------------------- | ----------------- |
| onclick       | on mouse click                              | onevent, mouse    |
| oncopy        | when all or some text is copied.            | onevent, mouse    |
| onmouseover   | when the mouse is hovered over the element. | onevent, mouse    |
| onkeydown     | when a keyboard key is pressed              | onevent, keyboard |
| onkeyup       | when a keyboard key is released             | onevent, keyboard |
| onload        | when loaded                                 | onevent,  window  |
| onsubmit      | when form is submitted using submit button                                            |                   |


oneven properies are named on + event, easy to remember.

document.body === document.querySelector("body")

Don't use in-line HTML event handlers. I'm not even going to include it.

### Using event handlers in JS files
Assume the following JS is linked in the head:
```js
// User Interface Logic
let h1 = document.querySelector("h1");
h1.onmouseover = function() {
  window.alert("I am a heading element.");
};

let p = document.querySelector("p");
p.onmouseover = function() {
  document.querySelector("p>em").innerText = "Don't be surprised";
};

let img = document.querySelector("img");
img.onmouseover = function() {
  img.style.height = "700px";
};
```
When this loads, we get the error:
```
Uncaught TypeError: Cannot set properties of null (setting 'onmouseover')
    at scripts.js:3:16
```

This is because the JS file is linked in the head, and loads before the rest of the HTML loads. The JS loads first, and looks for `<h1>` which doesn't exist yet. However, we should keep JS files in the head.

The following waits for the web page to load before loading the scripts in its body.
```js
window.onload = function() {
	//function body
};
```
This is a good place for event handlers.

document.getElementByID("ID").blah.blah
document.getElementByClassName("CLASSNAME").blah.blah

```js
function(e){
	event.preventDefault ();
};
```

```js
if (!input1 || !hinput2)  {

      //what to do if one of the inputs is missing (error)

    } else {

	//what we want to do

	};
```

```js
  target.addEventListener ("TYPE", function() {

    //callback function
    //or, w hat we want to run as the reaction event

  });
```

Can call a function like this, useful for onevent
```js
let h1 = document.querySelector("h1");
function alertHeading() {
  window.alert("This is a heading element.");
}
h1.onclick = alertHeading;
```

Similarly, can call an event handler like this 
```js
// using a function declaration
let h1 = document.querySelector("h1");
function alertHeading() {
  window.alert("This is a heading element.");
}//function declaration

h1.addEventListener("click", alertHeading); //pass click type and alertHeading function 
```

re-using functions 
```js
let h1 = document.querySelector("h1"); 
let h2 = document.querySelector("h2"); 
let h3 = document.querySelector("h3"); 
let h4 = document.querySelector("h4"); 
let h5 = document.querySelector("h5"); 
let h6 = document.querySelector("h6"); 

function alertHeadings() { //this type of declaration is hoisted
  window.alert("This is a heading element.");
}

//can use this in stead
	const alertHeadings = function() { //this type of declaration is not hoisted
	  window.alert("This is a heading element.");
	}


h1.addEventListener("click", alertHeadings);
h2.addEventListener("click", alertHeadings);
h3.addEventListener("click", alertHeadings);
h4.addEventListener("click", alertHeadings);
h5.addEventListener("click", alertHeadings);
h6.addEventListener("click", alertHeadings);
```

Removing an event listener - MUST have same arguments used to create
```js
h1.removeEventListener("click", alertHeading);
```


## Spread Operator ( . . . )
---
The opposite of rest
"Expands" an array into its elements
Often used to duplicate objects, or merge multiple objects together
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

### Copying
Coyping in Javascript creates a "shallow clone" of the object. It's not a new object in memory.
```js
const myCat = {
	name: "Murphy",
	age: 1
}

//we can just copy the myCat, or we can change or add properties.
const anotherCat = {...myCat, age: 2, color: "gray and white"};
```

### Merging
```js
const flagColor1 = {
  color1: "green"
}

const flagColor2 = {
  color2: "gold"
}

const flagColor3 = {
  color3: "black"
}

const jamaicanFlag = {...flagColor1, ...flagColor2, ...flagColor3}
```

```js
jamaicanFlag{
	color1: "green",
	color2: "gold", 
	color3: "black"
}
```

Be careful!
```js
const flagColor1 = {
  color1: "green" <<
}

const flagColor2 = {
  color1: "gold" <<
}

const flagColor3 = {
  color1: "black" <<
}

const jamaicanFlag = {...flagColor1, ...flagColor2, ...flagColor3}
```

```js
jamaicanFlag{
	color1: "black"
}
```

### Object.assign()
```js
Object.assign(ObjectToBeCopied, each, other, object, that, should, be, merged, with, the, object);
```

```js
const flagColor1 = {
  color1: "green"
}

const flagColor2 = {
  color2: "gold"
}

const flagColor3 = {
  color3: "black"
}

const jamaicanFlag = Object.assign({}, flagColor1, flagColor2, flagColor3);
```

### Combine arrays
```js
const array = [1,2];
const array2 = [3,4];
const array3 = [...array, ...array2];
```

```js
> array3
[1, 2, 3, 4]
```

### Passing arguments into functions
Passing array items into a function as argumentS, not as a single array:
```js
const array = [1, 2, 3];
spreadArgs(...array);
```

## Composition
What an object *can do* not what an object is.
```js
const canEat = function(creature) {
  const obj = {
    eat: function(food) {
      return `The ${creature} eats the ${food}.`
    }
  }
  return obj;
}
```
There is a function literal that returns an object. 
The object has a single property called `eat` that stores a function.

Create a cat:
```js
> const cat = canEat("cat");
```
Cat Object is now:
```js
{
  eat: function(food) {
        return `The cat eats the ${food}.`
      }
}
```
Cat can now eat food:
```js
> cat.eat("salmon");
'The cat eats the salmon.'
```

Define another method (sleep), and m ake a method that combines both
```js
const canEat = function(creature) {
  const obj = {
    eat: function(food) {
      return `The ${creature.name} eats the ${food}.` 
    }
  }
  return obj;
}

const canSleep = function(creature) {
  const obj = {
    sleep: function() {
      return `The ${creature.name} sleeps.` 
    }
  }
  return obj;
}

const sleepingEatingCreature = function(name) {
  let state = {
    name
  }

  return { ...state, ...canEat(state), ...canSleep(state) };
}
```
Implicit Return - If we use arrow notation with a function that returns a single object, we don't need to add areturn statement.

Ex:
```js
> const platypus = sleepingEatingCreature("platypus");

platypus {
  name: 'platypus', 
  eat: function(food) {
    return `The ${creature.name} eats the ${food}.`
  }, 
  sleep: function() {
    return `The ${creature.name} sleeps.`
  }
}

```


