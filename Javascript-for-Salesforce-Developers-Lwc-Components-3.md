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
````
const nodeList = document.querySelectorAll('p'); // NodeList
const paragraphArray = Array.from(nodeList); // Convert NodeList to an array
````
