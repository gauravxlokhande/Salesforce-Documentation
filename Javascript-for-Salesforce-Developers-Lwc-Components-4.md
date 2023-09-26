<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

# functions in JS:

## Defining a parameterize Function:
```
function greet(name) {
  console.log("Hello, " + name + "!");
}

greet("John"); // Outputs: "Hello, John!"
```

## Function Return Values:
```
function add(a, b) {
  return a + b;
}

const result = add(3, 5); // result will be 8
```
## Arrow Functions :
```
const square = (x) => x * x;

const result = square(4); // result will be 16
```

## Assign function to variable
```
const add = function(a, b) {
  return a + b;
};

const result = add(3, 5); // result will be 8
```

## Function taking multiple Arguments

```
// Define a function named "multiply" that takes any number of arguments and multiplies them
function multiply(...numbers) {
  let result = 1;
  for (let number of numbers) {
    result *= number;
  }
  return result;
}

// Call the "multiply" function with different numbers of arguments
let result1 = multiply(2, 3, 4);      // Result: 24
let result2 = multiply(5, 6);         // Result: 30
let result3 = multiply(10);           // Result: 10

console.log(result1, result2, result3);
```
##  Show Arguments 
```
function displayArguments() {
    console.log(arguments[0]);
}

displayArguments(1, "Hello", true);
```

## Nested Function 
```
function outerFunction() {
  const outerVariable = "I am from outerFunction";

  function innerFunction() {
    const innerVariable = "I am from innerFunction";
    console.log(outerVariable); // Accesses outerVariable from the outer function
    console.log(innerVariable); // Accesses innerVariable from the inner function
  }

  return innerFunction;
}

const innerFunc = outerFunction(); // innerFunc now holds a reference to innerFunction
innerFunc(); // Calls innerFunction and outputs both variables
```

## Self calling function

```
let name = function () {
    console.log("hii")
} ();
```
<br/>

# Arrow Functions In Js

## Arrow function with one parameter:
```
const square = (x) => x * x;
console.log(square(5)); // Output: 25
```

## Arrow function with multiple parameters:
```
const add = (a, b) => a + b;
console.log(add(3, 7)); // Output: 10
```

## Arrow function with no parameters:
```
const greet = () => "Hello, world!";
console.log(greet()); // Output: Hello, world!
```

## Arrow function with a block body:

```
const multiply = (a, b) => {
  let result = a * b;
  return result;
};
console.log(multiply(4, 6)); // Output: 24
```
## Arrow function in object

```
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: () => {
    return `${this.firstName} ${this.lastName}`;
  },
  sayHello: () => {
    console.log(`Hello, ${this.fullName()}!`);
  }
};

console.log(person.fullName()); // Output: undefined undefined
person.sayHello(); // Output: Hello, undefined undefined!
```

