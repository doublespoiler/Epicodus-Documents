# JAVASCRIPT CHEATSHEET

- [JAVASCRIPT CHEATSHEET](#javascript-cheatsheet)
  - [Data Types](#data-types)
    - [Primitives](#primitives)
    - [Numbers](#numbers)
    - [Strings](#strings)
    - [Objects](#objects)
  - [Declarations](#declarations)
  - [Operators](#operators)
  - [Functions](#functions)
    - [Declaring a function](#declaring-a-function)
    - [Calling a function](#calling-a-function)
    - [Built-in functions](#built-in-functions)
  - [Methods](#methods)
    - [Built-in methods](#built-in-methods)
    - [Prototype Methods](#prototype-methods)
  - [Arguments](#arguments)
  - [Other](#other)
    - [Conventions](#conventions)
  
## Data Types

### Primitives

Can only reprsent a single type and piece of data

| Name | Description | Example | Notes |
|----|----|----|----|
| Number | Just a number | `const myNumber=5;`| |
| String | Text | `const myString = "Hello.";`| Must be in quotes |
| Boolean | true/false | `const myBool = true;` | |
| Null | no value yet | `let myVar = null;` | We will change it later|
| Undefined | no value | | |
| Symbol | unique primitive | | |
| BigInt | Very large number | 2^52, etc. | |

[TOP](#javascript-cheatsheet)

### Numbers

- Expressions return a value (math)
- NaN - Not a number (but it's technically a number in JS)
- Infinity - Dividing a number by 0 (also technically a number in JS)*

[TOP](#javascript-cheatsheet)

### Strings

| Name | Description | Example | Notes |
|----|----|----|----|
| `\` | escape | `"Quoth the raven, \"Nevermore.\"";` | Tells JS the next character is just a character in the string|
| `'"text"'` | single quotes | `'"programming is fun!", she exclaimed.';` | Allows you to use "" for quotes inside |

[TOP](#javascript-cheatsheet)

### Objects

Containers for related data, and its functionality
Ex: Animal object, contains data about height, color, eating, meowing, etc.
Ex: Computer object, contains data about GPU, CPU, playing games, browsing web, etc.

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

[TOP](#javascript-cheatsheet)

## Declarations

| code | description | example | notes |
|----|----|----|----|
| var | variable | `var myNumber = 0;` | Old, don't use |
| let | variable | `let myNumber = 0;` | Use instead of var, indicates the variable will change, will not let you double declare |
| const | constant | `const myConstant = 0;` | cannot change, value must be declared, will not let you double declare |

[TOP](#javascript-cheatsheet)

## Operators

| symbol | name | example | notes |
| ---- | ---- | ---- | ---- |
| = | assignment| `const favoriteNumber = 42;` | sets variable equal to value |
| + | concatenation (addition) | `1 + 3`, `"I love " + "strings."'` | |
| -, * , / | arithmetic | It's just like math | |
| +=, -=, *=, /= | arithmetic assignment | `myVar += 1'` | does arithmetic and assigns at the same time |
| < | comparator less than | `5 < 10;` | returns boolean |
| <= | comparator less than equal to | `5 <= 10;` | returns boolean |
| > | comparator greater than | `5 > 10;` | returns boolean |
| >= | comparator greater than equal to | `5 >= 10;` | returns boolean |
| === | strict equality | check to see if two operands have the same value | `myNumber === 5'` | returns boolean |
| !== | strict ineequality | check to see if two operands have the different values | `myNumber !== 5'` | returns boolean |
| == | equality | check to see if two operands have the same value | `myNumber == 5'` | attempts to compare operands that are of different data types, returns boolean DO NOT USE |
| != | inequality | check to see if two operands have different values | `myNumber != 5'` | attempts to compare operands that are of different data types, returns boolean DO NOT USE |
| typeof | returns the data type | `typeof myString;` | returns as string |

[TOP](#javascript-cheatsheet)

## Functions 

A bundle of code that performs a set of procedures
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
function functionNameInCamelCase(acceptedParameter) { //curly brackets indicate body
  statement; //statements end with semicolon;
  statement; //We can call
  return; //use return o make the data inside the function available outside of it
} //no semicolon!
```
[TOP](#javascript-cheatsheet)

### Calling a function

```js
addEmphasis("I love my pet rabbit");
```

```js
functionName(functionArgument);
```

[TOP](#javascript-cheatsheet)

### Built-in functions

| code | description | example | arguments | notes |
| ---- | ---- | ---- | ---- | ----- |
| console.log | returns argument to console | `console.log("hello world");` | any | useful for debugging |

[TOP](#javascript-cheatsheet)

## Methods 

A type of function that belongs to a specific type of data
We **call** a method **on** something (the **reciever**) (including *variables*), asking the method to perform its actions on the data type it belongs to (it can only call that data type)
Can string methods together `"This is a string".concat("!!!", " I like strings!").toUpperCase();` (they go in order) - returns "THIS IS A STRING!!! I LIKE STRINGS!"
Hint: the "." means "called on," this is how you identify methods vs functions!

[TOP](#javascript-cheatsheet)

### Built-in methods 

| code | description | example | arguments | notes |
| ---- | ---- | ---- | ---- | ----- |
| toUpperCase | returns string in all Uppercase | `"This is a string.".toUpperCase();` | none | can be called on ANY string |
| toLowerCase | returns string  in all lowercase | `"HELLO".toLowerCase();` | none | can be called on any string | 
| conCat | returns string with concat argument on the end | `"This is a string".concat("!!!");` | string to attach | ex: returns "This is a string!!!", accepts multiple arguments |
| charAt | returns characer at arg (number) | `"caterpiller".charAt(5)'` | number | first character is 0 |
| toString | returns as string| `numberVar.toString();` | any | |
| toFixed | returns number as string with indicated number of decimals | `42.222.toFixed(2);` | number | returns 42.22 |
| parseInt | attempts to turn string into number | `myAge = parseInt("45");` | string | returns number, NaN if string isn't a number |

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

## Other


`myNumber += 5;` increments myNumber by 5
Statements do not reurn variables
`// comment`
`/* inline comment */`

### Conventions

- use `let` or `const` to declare variables
- use lower camelCase in variableNames
- use descriptive names for variables
- use semicolons after statements and expressions
- statements can be made of expressions
- expressions evaluate a value
- statements perform actions
- don't add a semicolon at the end of function delcaration

[TOP](#javascript-cheatsheet)