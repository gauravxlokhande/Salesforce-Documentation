<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

## functions in JS:

# Defining a parameterize Function:
```
function greet(name) {
  console.log("Hello, " + name + "!");
}

greet("John"); // Outputs: "Hello, John!"
```
#Function Return Values:
```
function add(a, b) {
  return a + b;
}

const result = add(3, 5); // result will be 8
```
# Arrow Functions :
```
const square = (x) => x * x;

const result = square(4); // result will be 16
```

# Assign function to variable
```
const add = function(a, b) {
  return a + b;
};

const result = add(3, 5); // result will be 8
```

# Nested Function 
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
