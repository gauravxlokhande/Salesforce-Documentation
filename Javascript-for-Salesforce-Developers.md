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

