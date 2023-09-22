<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

# JavaScript Variables

In JavaScript, variables are used to store and manage data. Variables are like containers that hold values, and you can give them names so you can reference and manipulate those values later in your code. 
some important things know about variables in JavaScript:

## Variable Declaration

You declare a variable using the `var`, `let`, or `const` keyword. The choice of which keyword to use depends on how you want the variable to behave.

- `var`: Variables declared with `var` are function-scoped, meaning they are only accessible within the function they are defined in (or globally if declared outside of any function). However, they have some quirks and no longer recommended in modern JavaScript.

- `let`: Variables declared with `let` are block-scoped, which means they are only accessible within the nearest enclosing curly braces (`{}`). `let` allows you to reassign values to the variable.

- `const`: Variables declared with `const` are also block-scoped, but their values cannot be reassigned once they are set. This is useful for defining constants.


```javascript
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



// JavaScript Map Functions

// Create a Map
const myMap = new Map();

// Add key-value pairs
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');

// Get a value by key
const value = myMap.get('key1'); // Retrieves 'value1'

// Check if a key exists
const keyExists = myMap.has('key3'); // Returns false

// Delete a key-value pair
myMap.delete('key2'); // Deletes the 'key2' entry

// Clear all entries
myMap.clear(); // Removes all entries from the map

// Get the number of entries
const mapSize = myMap.size; // Returns the number of entries

// Iterate through keys
const keysIterator = myMap.keys();
for (const key of keysIterator) {
  console.log(key); // Iterates through keys
}

// Iterate through values
const valuesIterator = myMap.values();
for (const value of valuesIterator) {
  console.log(value); // Iterates through values
}

// Iterate through key-value pairs
const entriesIterator = myMap.entries();
for (const [key, value] of entriesIterator) {
  console.log(`Key: ${key}, Value: ${value}`);
}

// Additional Map Functions

// Map.prototype.forEach(callbackFn[, thisArg])
// Executes a provided function once for each key-value pair in the Map, in insertion order.
myMap.set('name', 'Alice');
myMap.set('age', 30);
myMap.forEach((value, key) => {
  console.log(`Key: ${key}, Value: ${value}`);
});

// Map.prototype[Symbol.iterator]()
// Returns a new Iterator object that contains an array of [key, value] for each element in the Map object.
const mapEntries = [...myMap];
console.log(mapEntries);

// Map.prototype.get(key)
// Returns the value associated with the specified key or undefined if the key does not exist.
const nonExistentValue = myMap.get('nonExistentKey'); // Returns undefined


