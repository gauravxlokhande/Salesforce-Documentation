<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

## Arrays In JS

# Creating an Array:

```
const emptyArray = [];
```

```
const fruits = ["apple", "banana", "cherry"];
const numbers = [1, 2, 3, 4, 5];
const mixedArray = [1, "apple", true, { name: "John" }];
```

```
const fruits = ["apple", "banana", "cherry"];
console.log(fruits[0]); // Outputs: "apple"
console.log(fruits[1]); // Outputs: "banana"
```

```
const fruits = ["apple", "banana", "cherry"];
fruits[1] = "orange";
console.log(fruits); // Outputs: ["apple", "orange", "cherry"]
```
```
const arrayWithLength = new Array(5); // Creates an array with 5 undefined elements
```
```
const sourceArray = [1, 2, 3];
const newArray = [...sourceArray]; // Creates a copy of sourceArray
```
```
const numbers = new Array(1, 2, 3, 4, 5);

console.log(numbers); // Outputs: [1, 2, 3, 4, 5]
```

## Array Methods

# Important for => LWC
# Array.from
```
// Assuming you have a NodeList of <p> elements
const nodeList = this.template.querySelectorAll('p'); // NodeList
const paragraphArray = Array.from(nodeList); // Convert NodeList to an array

paragraphArray.forEach((element) => {
  // Perform actions on each element in the array
});
```

# .Concat()
```
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const mergedArray = array1.concat(array2);
console.log(mergedArray); // Outputs: [1, 2, 3, 4, 5, 6]
```
# Array.from()
```
// Create an array-like object (e.g., a string)
const str = "Hello";

// Use Array.from() to convert it into an array
const charArray = Array.from(str);

console.log(charArray); // Outputs: ["H", "e", "l", "l", "o"]

```
```
// Create a Set
const mySet = new Set([1, 2, 3, 4, 5]);

// Use Array.from() to convert the Set into an array
const arrayFromSet = Array.from(mySet);

console.log(arrayFromSet); // Outputs: [1, 2, 3, 4, 5]
```

# Array.isArray()
```
const arr = [1, 2, 3];
const obj = { key: 'value' };

console.log(Array.isArray(arr)); // Outputs: true
console.log(Array.isArray(obj)); // Outputs: false
```

# .includes

```
const numbers = [1, 2, 3, 4, 5];

console.log(numbers.includes(3)); // Outputs: true
console.log(numbers.includes(6)); // Outputs: false

// Using fromIndex
console.log(numbers.includes(3, 2)); // Outputs: true (search from index 2)
```

# .Join
```
const fruits = ["apple", "banana", "cherry"];

const dashSeparated = fruits.join("-");
console.log(dashSeparated); // Outputs: "apple-banana-cherry"

const spaceSeparated = fruits.join(" ");
console.log(spaceSeparated); // Outputs: "apple banana cherry"
```

# .push() 

```
const fruits = ["apple", "banana", "cherry"];
const newLength = fruits.push("date");

console.log(fruits); // Outputs: ["apple", "banana", "cherry", "date"]
console.log(newLength); // Outputs: 4 (the new length of the array)
```

# .Pop()
```
const fruits = ["apple", "banana", "cherry"];
const removedFruit = fruits.pop();

console.log(fruits); // Outputs: ["apple", "banana"]
console.log(removedFruit); // Outputs: "cherry"
````

# .reverse()
```
const fruits = ["apple", "banana", "cherry"];
fruits.reverse();

console.log(fruits); // Outputs: ["cherry", "banana", "apple"]
```

# .Shift()
```
const fruits = ["apple", "banana", "cherry"];
const removedFruit = fruits.shift();

console.log(fruits); // Outputs: ["banana", "cherry"]
console.log(removedFruit); // Outputs: "apple"
```

# .Unshift()
```
const fruits = ["banana", "cherry"];
const newLength = fruits.unshift("apple");

console.log(fruits); // Outputs: ["apple", "banana", "cherry"]
console.log(newLength); // Outputs: 3 (the new length of the array)
```

# .Slice()
```
const numbers = [1, 2, 3, 4, 5];

const sliced1 = numbers.slice(1, 4); // Extracts elements at indices 1, 2, and 3
console.log(sliced1); // Outputs: [2, 3, 4]

const sliced2 = numbers.slice(2); // Extracts elements from index 2 to the end
console.log(sliced2); // Outputs: [3, 4, 5]

const sliced3 = numbers.slice(-3); // Extracts the last 3 elements
console.log(sliced3); // Outputs: [3, 4, 5]
```

# .Splice()

```
array.splice(start[, deleteCount[, item1[, item2[, ...]]]]);
```
```
const fruits = ["apple", "banana", "cherry", "date"];

// Remove elements at index 1 and 2 (banana and cherry)
const removed = fruits.splice(1, 2);
console.log(fruits); // Outputs: ["apple", "date"]
console.log(removed); // Outputs: ["banana", "cherry"]

// Insert "kiwi" and "grape" at index 1, replacing 0 elements
fruits.splice(1, 0, "kiwi", "grape");
console.log(fruits); // Outputs: ["apple", "kiwi", "grape", "date"]

// Replace "date" with "fig" at index 3
fruits.splice(3, 1, "fig");
console.log(fruits); // Outputs: ["apple", "kiwi", "grape", "fig"]
```

# .toString()

```
const fruits = ["apple", "banana", "cherry"];
const fruitsString = fruits.toString();

console.log(fruitsString); // Outputs: "apple,banana,cherry"
```

# .Values()
```
const fruits = ["apple", "banana", "cherry"];
const iterator = fruits.values();

console.log(iterator.next().value); // Outputs: "apple"
console.log(iterator.next().value); // Outputs: "banana"
console.log(iterator.next().value); // Outputs: "cherry"
console.log(iterator.next().value); // Outputs: undefined
```
