# Functional Programming
---
## Function Literals
An expression that defines an unnamed function 
Can use to assign a function to a variable.
```js
var myFunction = function(args)
{
	return "does a thing";
}
```

## Pure Functions
---
Given a single specific input, pure functions always return the same output
```js
function addOne(num) {
  return num + 1;
}
```
No randomness
Always returns an output
Cannot have side effects
Cannot rely on external variables or state

## Functions as first-class citizens
---
You can use functions in the same way you use variables

### Callback 
pass a function through another function as an argument
```js
function add(num1, num2) {
  return num1 + num2;
}

function printResult(sum) {
  return \`The value of this equation is ${sum}.`
}
```

```js
printResult(add(5, 7));
> 12
```

### Function Expression  
Assign function as a variable
```js
const funkyVariable = function(arg) {
	return arg;
}
```

```js
funkyVariable("Hello!");
> "Hello!"
```

Higher Order Function - Returning a function
```js
function doAThing() {
  return function() {
    return "A thing was done."
  }
}
```

```js
doAThing()
> "A thing was done."
```
## Closure
---
An inner function that has access to the variables from an outer function

```js
function welcome(salutation) {
  return function(yourName) {
    return `${salutation}! Nice to meet you, ${yourName}!`
  }
}

const heyThere = welcome("Hey there"); 

function heyThere(yourName){
	return `Hey there, ${yourName}!`
}

const spanishGreeting = welcome("Buenos Dias!");
```

```js
> heyThere("Joe"); 
"Hey there! Nice to meet you, Joe!"
> spanishGreeting("Mary"); 
"Buenos Dias! Nice to meet you, Mary!"
```

double nested
```js
function nameEnhancer(prefix){
  return function(suffix){
    return function(name){
      return `${prefix} ${name} ${suffix}`;
    }
  }
}

//pay attention to the order
const misterJunior = nameEnhancer("Mister")("Junior");
const duchessThird = nameEnhancer("Duchess")("The Third");
```
#### EX2:
```js
const multiplier = (x) => {
  return (y) => {
    return x * y;
  }
}

const doubler = multiplier(2);
const tripler = multiplier(3);
const quadrupler = multiplier(4);

```

```js
> doubler(2);
4
> tripler(5); 
15
> quadrupler(2);
8
 ```

## Currying
---
To Curry - Take a function with multiple arguments and rewrite it as a series of functions, each with only 1 argument

Unary function -  A function with only 1 argument

Uncurried:
```js
function aThingIMaybeLike(howmuchILikeIt, thing, reason){
	return `I ${howMuchILikeIt} ${thing} because ${reason}.`;
}
```

```js
> aThingIMaybeLike("really like", "functional programming", "it's cool"); 
"I really like functional programming because it's cool."
```
Curried:
```js
function aThingIMaybeLike(howMuchILikeIt) {
  return function(thing) {
    return function(reason) {
      return `I ${howMuchILikeIt} ${thing} because ${reason}.`;
    }
  }
}
const thingsThatBugMe = aThingIMaybeLike("do not like");
const reasonILoveCoding = aThingIMaybeLike("love")("coding");
```

```js
> aThingIMaybeLike("really like")("functional programming")("it's cool");
"I really like functional programming because it's cool."

> thingsThatBugMe("functions with side effects")("they break code");
"I do not like functions with side effects because they break code."

> reasonILoveCoding("it is fun");
"I love coding because it is fun."
```

## Recursion
---
```js 
This is a for loop to count to 3 written recursively
const incrementCounter = (counter) => {
  if (isNaN(counter)) { // This is the termination condition
    return;
  }
  if (counter >= 3) { //This is the base case
    return counter;
  } else {  //this is the recursion
    console.log(counter);
    return incrementCounter(counter + 1);
  }
}
```

```js
incrementCounter() {
  // This call will complete last.
  return incrementCounter() {
    // This call will complete second.
    return incrementCounter() {
      // This call will complete first.
    }
  }
}
```


## State
---
Anything we are asking a computer to remember
Like a "snapshot" of the application at any given time
Functional programming wants to avoid mutating state
	pure functions
	avoid side effects
	immutable
	stateless

### State management patterns
Observer Pattern
	When an object keeps track of dependents (observers) that listen for changes
	When the state of the object changes, it notifies the observer
	Code triggers when the object changes
	Allows code to be loosely coupled
Pubsub pattern (Redux)
	More complex than observer pattern
	Concept of publishing and subscribing
	There is an intermediary between observers and objects
	An object can publish to the intermediary
	An observer subscribe to the intermediary
	Objects and observers don't need to know anything at all

#### Storing state in closures
Closures can be used to store basic state information
```js
const counterFunction = () => {
  let counter = 0;
  return () => {
    counter++;
    return counter;
  }
}
```

We can assign the function but we can't see the counter!
```js
> const incrementer = counterFunction();
incrementer() => {
	counter++;
	return counter;
}
```
But the counter still increases if we run the function multiple times. Notice the counter for incrementerTwo() and incrementer() are independent, as they have separate lexical scopes.
```js
> incrementer()
1
> incrementer()
2
> incrementer()
3
> const incrementerTwo = counterFunction();
> incrementerTwo()
1
> incrementerTwo()
2
> incrementer()
4
```
