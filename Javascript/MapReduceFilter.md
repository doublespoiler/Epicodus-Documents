# Map, Reduce, Filter
---

## map() 
---
returns a new array

Not using map()
```js
const numArray = [1, 2, 3, 4, 5];
let doubledArray = [];
numArray.forEach(function(element) {
  doubledArray.push(element * 2);
});
doubledArray;
```

Using map()
```js
const numArray = [1, 2, 3, 4, 5];
const doubledArray = numArray.map(function(element) {
  return element * 2;
});
doubledArray;

OR

const doubleArray = numArray.map(e =>  e * 2);
```

## reduce()
---
reduce an array to a single element
	find longest or shortest string in an array
	sum an array

```js
const numArray = [3, 7, 5];
const summedArray = numArray.reduce(function(currentValue, element) {
  return element + currentValue;
}, 0);

const toDos = friends.reduce(function(array, friend) {
  return array.concat(friend.wantToDo);
}, []);


const toDoTally = toDos.reduce(function(voteTally, toDo) {
  voteTally[toDo] = (voteTally[toDo] || 0) + 1;
  return voteTally;
}, {});

```

```js
currentValue is the currentValue of reduce()
```

## filter()
---
filter array or collection based on certain conditions
```js
const numArray = [7, 14, 32, 8];
const filteredArray = numArray.filter(e => e > 10);

const developers = employees.filter(e => e.role === "developer")

```