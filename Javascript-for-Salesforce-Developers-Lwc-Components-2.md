<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

## Objects In Javascript
object is basically used for store key and value so that developer need not to declear variable and datatype for every data.

<img width="834" alt="Screenshot 2023-09-22 125445" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components/assets/119065314/232ba7f3-a18d-4cbf-a637-41e73cc451f0">

<br/>

## Objects:

```
// Creating an empty object
const person = {};

// Adding properties to the object
person.firstName = "John";
person.lastName = "Doe";
person.age = 30;

// Accessing properties
console.log(person.firstName); // Outputs: "John"
console.log(person.lastName);  // Outputs: "Doe"
```

```
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};
```

```
const person = {
  firstName: "John",
  lastName: "Doe",
  sayHello: function() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}.`);
  }
};

// Calling the method
person.sayHello(); // Outputs: "Hello, my name is John Doe."
```

```
const person = {
  firstName: "John",
  lastName: "Doe",
  sayHello() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}.`);
  }
};

person.sayHello(); // Outputs: "Hello, my name is John Doe."
```


## Conditionals in JS

```
const age = 25;

if (age >= 18) {
  console.log("You are an adult.");
} else {
  console.log("You are a minor.");
}
```

```
const score = 75;

if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");
} else if (score >= 70) {
  console.log("C");
} else {
  console.log("F");
}
```

```
const day = "Tuesday";

switch (day) {
  case "Monday":
  case "Tuesday":
  case "Wednesday":
  case "Thursday":
  case "Friday":
    console.log("Weekday");
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend");
    break;
  default:
    console.log("Invalid day");
}
```

```
const age = 25;
const status = (age >= 18) ? "Adult" : "Minor";
console.log(status); // Outputs: "Adult"
```


## Loops in js

# Basic for Loop:
```
for (let i = 0; i < 5; i++) {
  console.log(i); // Outputs: 0, 1, 2, 3, 4
}
```
# for...in Loop:

```
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};

for (let key in person) {
  console.log(key + ": " + person[key]);
}
// Outputs:
// firstName: John
// lastName: Doe
// age: 30
```
# for...of Loop:
```
const colors = ["red", "green", "blue"];

for (let color of colors) {
  console.log(color);
}
// Outputs:
// red
// green
// blue
```

# for Each Loop in LWC-JS

```
 @track items = [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' },
  ];

  connectedCallback() {
    // Using forEach loop to iterate through the array
    this.items.forEach((item) => {
      console.log(item.name);
    });
  }
```

# while Loop:
```
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

```
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```


