<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

## A callback is a function that is passed as an argument to another function and is executed when that function completes its task. Callbacks allow you to manage the flow of code in scenarios where certain operations may take time to complete, such as reading a file, making an HTTP request, or handling user interactions.


## example of how callbacks work:

```
// Define a function called fetchData that takes a callback as an argument
function fetchData(callback) {
  // Simulate fetching data from a server (e.g., an HTTP request) with a delay of 1000 milliseconds (1 second)
  setTimeout(function() {
    // Create a data object representing the fetched data
    const data = { name: "John", age: 30 };
    
    // Execute the provided callback function with the fetched data as an argument
    callback(data);
  }, 1000);
}

// Define a function called processFetchedData that will be used as the callback
function processFetchedData(data) {
  // Log a message with the received data
  console.log(`Received data: ${data.name}, ${data.age} years old`);
}

// Call the fetchData function and provide processFetchedData as the callback
fetchData(processFetchedData);

```
In this example:

1. The fetchData function takes a callback function callback as an argument.
2. Inside fetchData, we simulate fetching data asynchronously using setTimeout.
3. Once the data is available, we call the callback function and pass the fetched data to it.

The processFetchedData function is used as the callback in this case, and it gets executed with the fetched data when the data retrieval is complete.


##  modified version of the previous example using Promises and async/await to achieve the same result:

```
// Define a function called fetchData
function fetchData() {
  // Return a Promise that encapsulates an asynchronous operation
  return new Promise(function(resolve) {
    // Simulate an asynchronous operation using setTimeout
    setTimeout(function() {
      // Once the operation is complete, resolve the Promise with data
      const data = { name: "John", age: 30 };
      resolve(data);
    }, 1000); // Wait for 1000 milliseconds (1 second)
  });
}

// Define an asynchronous function called processFetchedData
async function processFetchedData() {
  // Call the fetchData function and wait for it to resolve (await)
  const data = await fetchData();

  // After the Promise is resolved, log the received data
  console.log(`Received data: ${data.name}, ${data.age} years old`);
}

// Call the processFetchedData function to start the asynchronous process
processFetchedData();

```


## Classes In JS:

# A basic JavaScript class typically consists of the following components:

Class Declaration: This is where you declare the class using the class keyword, followed by the class name.

Constructor Method: A special method called constructor that initializes the object's properties when an instance is created.

Properties (Fields): Variables defined within the class that hold data.

Methods: Functions defined within the class that perform actions or provide behavior for the objects created from the class.

Basic template for defining a class in JavaScript:

```
class ClassName {
  // Constructor method for initializing properties
  constructor(property1, property2) {
    this.property1 = property1;
    this.property2 = property2;
  }

  // Method 1
  method1() {
    // Code for method 1
  }

  // Method 2
  method2() {
    // Code for method 2
  }
}
```

# Example:

```
class Person {
  // Constructor method for initializing properties
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  // Method to display information about the person
  displayInfo() {
    console.log(`Name: ${this.name}, Age: ${this.age}`);
  }
}

// Create an instance of the Person class
const person1 = new Person("Alice", 25);

// Access and use the properties and methods of the instance
console.log(person1.name); // Output: Alice
person1.displayInfo();     // Output: Name: Alice, Age: 25
```

# Inheritance:
```
class Superclass {
  // Superclass constructor and methods
}

class Subclass extends Superclass {
  // Subclass-specific properties and methods
}
```
# Example:

```
class Animal {
  constructor(name) {
    this.name = name;
  }

  makeSound() {
    console.log("Animal makes a sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call the superclass constructor
    this.breed = breed;
  }

  makeSound() {
    console.log("Dog barks");
  }
  // Subclass-specific methods
  fetch() {
    console.log("Dog fetches a ball");
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
console.log(myDog.name); // Output: Buddy
myDog.makeSound();       // Output: Dog barks
myDog.fetch();           // Output: Dog fetches a ball
```

