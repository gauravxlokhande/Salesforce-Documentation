<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

## JavaScript Variables

In JavaScript, variables are used to store and manage data. Variables are like containers that hold values, and you can give them names so you can reference and manipulate those values later in your code. 
some important things know about variables in JavaScript:

# Variable Declaration

You declare a variable using the `var`, `let`, or `const` keyword. The choice of which keyword to use depends on how you want the variable to behave.

- `var`: Variables declared with `var` are function-scoped, meaning they are only accessible within the function they are defined in (or globally if declared outside of any function). However, they have some quirks and no longer recommended in modern JavaScript.

- `let`: Variables declared with `let` are block-scoped, which means they are only accessible within the nearest enclosing curly braces (`{}`). `let` allows you to reassign values to the variable.

- `const`: Variables declared with `const` are also block-scoped, but their values cannot be reassigned once they are set. This is useful for defining constants.


```
function exampleScope() {
  // Variable declared with var - function-scoped
  var localVar = "I'm a local variable";
  
  if (true) {
    // Variable declared with let - block-scoped
    let blockVar = "I'm a block-scoped variable";
    
    // Variable declared with const - block-scoped
    const constVar = "I'm a constant variable";
  }
  
  // localVar is accessible here
  console.log(localVar); // Output: I'm a local variable
  
  // blockVar is not accessible here - causes an error
  console.log(blockVar); // Error: blockVar is not defined
  
  // constVar is not accessible here - causes an error
  console.log(constVar); // Error: constVar is not defined
}
```
<br/>
<br/>

## JavaScript Operators Cheatsheet
# Arithmetic Operators
- Addition: `+`
- Subtraction: `-`
- Multiplication: `*`
- Division: `/`
- Modulus (Remainder): `%`
- Increment: `++`
- Decrement: `--`


<br/>
<br/>

## Difference between == and ===
<img width="826" alt="Screenshot 2023-09-22 122357" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components/assets/119065314/9466fe00-743b-408e-8220-0013b3080e90">

```
var x =5;
var y ="5";
x == y; // true
x === y; // false 
```

<br/>
<br/>

## JavaScript Map 
<b>A JavaScript Map is a built-in data structure for storing key-value pairs, allowing various key types and preserving insertion order. A JavaScript Set is a built-in data structure for storing unique values.<b/>

```
// Create a Map
const myMap = new Map();
```
```
// Add key-value pairs
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
```
```
// Get a value by key
const value = myMap.get('key1'); // Retrieves 'value1'
```
```
// Check if a key exists
const keyExists = myMap.has('key3'); // Returns false
```
```
// Delete a key-value pair
myMap.delete('key2'); // Deletes the 'key2' entry
```
```
// Clear all entries
myMap.clear(); // Removes all entries from the map
```
```
// Get the number of entries
const mapSize = myMap.size; // Returns the number of entries
```
```
// Iterate through keys
const keysIterator = myMap.keys();
for (const key of keysIterator) {
  console.log(key); // Iterates through keys
}
```
```
// Iterate through values
const valuesIterator = myMap.values();
for (const value of valuesIterator) {
  console.log(value); // Iterates through values
}
```
```
// Iterate through key-value pairs
const entriesIterator = myMap.entries();
for (const [key, value] of entriesIterator) {
  console.log(`Key: ${key}, Value: ${value}`);
}
```
```
// Map.prototype.forEach(callbackFn[, thisArg])
// Executes a provided function once for each key-value pair in the Map, in insertion order.
myMap.set('name', 'Alice');
myMap.set('age', 30);
myMap.forEach((value, key) => {
  console.log(`Key: ${key}, Value: ${value}`);
});
```
```
// Map.prototype[Symbol.iterator]()
// Returns a new Iterator object that contains an array of [key, value] for each element in the Map object.
const mapEntries = [...myMap];
console.log(mapEntries);
```
```
// Map.prototype.get(key)
// Returns the value associated with the specified key or undefined if the key does not exist.
const nonExistentValue = myMap.get('nonExistentKey'); // Returns undefined
```
```
// LWC JavaScript code
import { LightningElement } from 'lwc';

export default class MyLWCComponent extends LightningElement {
  salesforceDataMap = new Map(); // Assuming you have populated this Map with Salesforce data

  // Function to iterate over the Map
  handleMapIteration() {
    this.salesforceDataMap.forEach((value, key) => {
      // Perform actions with each key and value pair
      console.log(`Key: ${key}, Value: ${value}`);
    });
  }
}
```

<br/>
<br/>

## JavaScript Set 
<b>JavaScript Sets can help to store and manage unique values efficiently. Sets ensure that each value is unique within the collection.<b/>

```
// Create a Set
const mySet = new Set();
```
```
// Add values
mySet.add('value1');
mySet.add('value2');
```
```
// Check if a value exists
const hasValue = mySet.has('value1'); // Returns true
```
```
// Delete a value
mySet.delete('value2'); // Deletes 'value2' from the set
```
```
// Clear all values
mySet.clear(); // Removes all values from the set
```
```
// Get the number of values
const setSize = mySet.size; // Returns the number of values
```
```
// Iterate through values
const setValuesIterator = mySet.values();
for (const value of setValuesIterator) {
  console.log(value); // Iterates through values
}
```

```
// LWC JavaScript code
import { LightningElement } from 'lwc';

export default class MyLWCComponent extends LightningElement {
  salesforceData = new Set(); // Assuming you have populated this Set with Salesforce data

  // Function to iterate over the Set
  handleSetIteration() {
    this.salesforceData.forEach((value) => {
      // Perform actions with each value
      console.log(value);
    });
  }
}
```




