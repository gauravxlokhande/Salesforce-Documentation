# Promises In JS:

## 1. Callback Function:

```
// Define a function that takes a callback as an argument
function doSomethingAsync(callback) {
    setTimeout(function () {
        console.log("Task is done!");
        callback(); // Call the callback function
    }, 2000); // Simulate an asynchronous operation (e.g., a network request)
}

// Define a callback function
function callbackFunction() {
    console.log("Callback function is called!");
}

// Call the function with the callback
doSomethingAsync(callbackFunction);
```

## 2. Promise and resolve

```
const myPromise = new Promise((resolve, reject) => {
    // Simulate an asynchronous operation
    setTimeout(() => {
        resolve("Success!"); // Resolve the Promise
        // If there was an error, you could call reject("Error message");
    }, 2000);
});

myPromise.then(
    (result) => {
        console.log("Fulfilled:", result); // Called when the Promise resolves
    },
    (error) => {
        console.error("Rejected:", error); // Called when the Promise is rejected
    }
);
```

```
const myPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("Error!"); // Reject the Promise
    }, 2000);
});

myPromise
    .then((result) => {
        console.log("Fulfilled:", result); // This won't be called
    })
    .catch((error) => {
        console.error("Rejected:", error); // Called when the Promise is rejected
    });
```


## 3. Async Await in js:

```
<!-- asyncAwaitExample.html -->
<template>
    <div>
        <template if:true={isLoading}>
            Loading...
        </template>
        <template if:false={isLoading}>
            <ul>
                <template for:each={data} for:item="item">
                    <li key={item.id}>{item.title}</li>
                </template>
            </ul>
        </template>
    </div>
</template>
```

```
// asyncAwaitExample.js
import { LightningElement, wire } from 'lwc';

export default class AsyncAwaitExample extends LightningElement {
    isLoading = true;
    data = [];

    // Wire the fetchData function to a property to make it reactive
    @wire(fetchData)
    wiredData({ error, data }) {
        if (data) {
            this.data = data;
            this.isLoading = false;
        } else if (error) {
            console.error(error);
            this.isLoading = false;
        }
    }
}

// Function to fetch data asynchronously
async function fetchData() {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    if (!response.ok) {
        throw new Error('HTTP request failed');
    }
    const data = await response.json();
    return data;
}
```

