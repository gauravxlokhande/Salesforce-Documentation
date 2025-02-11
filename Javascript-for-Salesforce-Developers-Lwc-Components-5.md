<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

# Console Methods in JS:

## JavaScript provides a set of built-in methods that you can use to interact with the console in your web browser's developer tools or in server-side JavaScript environments. These methods are useful for debugging, logging, and providing feedback during development.


1. console.log(): Prints a message or an object to the console. This is one of the most commonly used console methods for debugging.

```
console.log("Hello, world!");
```
2. console.error(): Logs an error message to the console with an error icon. Useful for highlighting critical issues.

```
console.error("This is an error message.");
```
3. console.warn(): Logs a warning message to the console with a warning icon. Used for non-fatal issues that should be addressed.
```
console.warn("This is a warning message.");
```
4. console.info(): Logs an informational message to the console with an info icon. Useful for general information.
```
console.info("This is an informational message.");
```
5. console.table(): Displays tabular data as a table. Useful for visualizing arrays or objects with structured data.

```
const data = [
  { name: "Alice", age: 30 },
  { name: "Bob", age: 25 },
];

console.table(data);
```
6. console.group() and console.groupEnd(): Groups related log messages together, making it easier to organize and collapse logs in the console.

```
console.group("Group 1");
console.log("Log 1");
console.log("Log 2");
console.groupEnd();

console.group("Group 2");
console.log("Log 3");
console.groupEnd();
```

7. console.count(): Counts the number of times a particular log message is called. Useful for tracking how many times a function or event occurs.

```
for (let i = 0; i < 5; i++) {
  console.count("Loop iteration");
}
```

8. console.time() and console.timeEnd(): Measures the time elapsed between the start and end of a code block. Useful for performance profiling.

```
console.time("Timer");
// Code to be timed
console.timeEnd("Timer");
```

9. console.clear(): Clears the console, removing all previous log messages and errors.

```
console.clear();
```



# setTimeout and setInterval functions:

## In JavaScript, setTimeout and setInterval are two functions that allow you to execute code at a specified delay or at regular intervals. These functions are commonly used for tasks like animations, periodic updates, and asynchronous operations. 

1. setTimeout:
```
setTimeout(function() {
  console.log("This will be executed after 2000 milliseconds (2 seconds).");
}, 2000);
```

```
setTimeout(() => {
  console.log("This will be executed after 1000 milliseconds (1 second).");
}, 1000);
```


2. setInterval:

```
let counter = 0;

const intervalId = setInterval(function() {
  console.log(`Interval ${counter}`);
  counter++;

  if (counter === 5) {
    clearInterval(intervalId); // Stop the interval after 5 iterations
  }
}, 1000);
```

```
const timeoutId = setTimeout(function() {
  console.log("This will not be executed.");
}, 2000);

clearTimeout(timeoutId); // Cancels the timeout
```


```
const intervalId = setInterval(function() {
  console.log("This will not continue indefinitely.");
}, 1000);

// After some condition is met, stop the interval
clearInterval(intervalId);
```


