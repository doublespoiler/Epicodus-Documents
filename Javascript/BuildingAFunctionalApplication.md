# Building a Functional Application
---
## Object-oriented vs Functional

```js

class Plant{
	constructor(){
	this.water = 0;
	this.soil = 0;
	this.light = 0;
	}
}
//Object Oriented Approach
  hydrate() {
    this.water ++
  }

  feed() {
    this.soil ++
  }

  giveLight() {
    this.light ++
  }
}

//Functional approach
const hydrate = (plant) => { //takes a plant object
  return { //returns a new object
    ...plant, //that is a copy of the plant
    water: (plant.water || 0) + 1 //and takes the plant's water (or 0) and adds 1 to it. ||0 is used as the default value if plant.water = NaN
  }
};
const feed = (plant) => {
  return {
    ...plant,
    soil: (plant.soil || 0) + 1
  }
};
const light = (plant) => {
	return {
	...plant,
	soil: (plant.soil || 0) + 1
	}
}

- [x] ///This function would take a plant and any property and +X that property, it's even better than before because it combines all 3 functions into 1, and lets us pick value, and it is curried!


const changeState = (prop) => {
  return (value) => {
    return (state) => ({
      ...state,
      [prop] : (state[prop] || 0) + value
    })
  }
}

const feed = changeState("soil");
const hydrate = changeState("water");
const giveLight = changeState("light");


const blueFood = changeState("soil")(5);
const greenFood = changeState("soil")(10);
const yuckyFood = changeState("soil")(-5);


```

```js

> let plant = { soil: 0, light: 0, water: 0 }
> changePlantState(plant, "soil")
{soil: 1, light: 0, water: 0}

```

## Storing State
```js
const storeState = () => { //does not take an argument, is only used to store currentState
  let currentState = {soil: 0, light: 0, water: 0}; //initialized as an empty object
  return (stateChangeFunction) => { //takes a function as argument
    const newState = stateChangeFunction(currentState);  //new state after the change, so we do not mutate currentState
    currentState = {...newState}; //breaking the rules! Make a copy of newState and assign it to currentState
    return newState; //return the newState. In this case, either is ok since they are the same.
  }
}


const stateControl = storeState();

```

It stores state!
```js

const fedPlant = stateControl(blueFood);
> { soil: 5, light: 0, water: 0}

const plantFedAgain = stateControl(greenFood);
> { soil: 15, light: 0, water: 0 }

```

If you need to set initial properties: 
```js

const storeState = (initialState) => {
  let currentState = initialState; // We could pass in an initial state to the object instead of starting with an empty object as well.
  return (stateChangeFunction) => {
    const newState = stateChangeFunction(currentState);
    currentState = {...newState};
    return newState;
  }
}

```

To have the function be able to access and store state
```js
const storeState = () => {
  let currentState = {};
  return (stateChangeFunction = state => state) => { //if stateChangeFunction is null, state == state (so it doesn't change, just access!)
    const newState = stateChangeFunction(currentState);
    currentState = {...newState};
    return newState;
  }
}
```

Final application
```js
// This function stores our state.
const storeState = () => {
    let currentState = {};
    return (stateChangeFunction = state => state) => {
      const newState = stateChangeFunction(currentState);
      currentState = {...newState};
      return newState;
    }
  }

const stateControl = storeState();

// This is a function factory. 
// We can easily create more specific functions that 
// alter a plant's soil, water, and light to varying degrees.
const changeState = (prop) => {
  return (value) => {
    return (state) => ({
      ...state,
      [prop] : (state[prop] || 0) + value
    })
  }
}

// We create four functions using our function factory. 
// We could easily create many more.
const feed = changeState("soil")(1);
const blueFood = changeState("soil")(5);

const hydrate = changeState("water")(1);
const superWater = changeState("water")(5);

window.onload = function() {

  // This function has side effects because we are manipulating the DOM.
  // Manipulating the DOM will always be a side effect. 
  // Note that we only use one of our functions to alter soil. 
  // You can easily add more.
  document.getElementById('feed').onclick = function() {
    const newState = stateControl(blueFood);
    document.getElementById('soil-value').innerText = `Soil: ${newState.soil}`;
  };

  // This function doesn't actually do anything useful in this application 
  // — it just demonstrates how we can "look" at the current state 
  // (which the DOM is holding anyway). 
  // However, students often do need the ability to see the current state 
  // without changing it so it's included here for reference.
  document.getElementById('show-state').onclick = function() {
    // We just need to call stateControl() without arguments 
    // to see our current state.
    const currentState = stateControl();
    document.getElementById('soil-value').innerText = `Soil: ${currentState.soil}`;
  };
};
```

```html
<html>
  <head>
    <script type="text/javascript" src="plant.js"></script>
    <title>Grow Your Plant</title>
  </head>
  <body>
    <button id="feed">Add soil</button>
    <button id="show-state">Current Stats</button>
    <h1>Your Plant's Values</h1>
    <h3><div id="soil-value">0</div></h3>
  </body>
</html>
```