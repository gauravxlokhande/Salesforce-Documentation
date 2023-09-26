<div align="center"> <h1>LWC-JS-Cheatsheet</h1></div>

# Async Await In LWC Realtime Example js:

```
import { LightningElement, track } from 'lwc';

export default class AsyncAwaitExample extends LightningElement {
    // Define tracked properties to store error and fetched data
    @track error;
    @track data;

    // Define an asynchronous lifecycle hook - connectedCallback
    async connectedCallback() {
        try {
            // Attempt to make an asynchronous HTTP GET request
            const response = await fetch('https://jsonplaceholder.typicode.com/posts');

            // Check if the HTTP response is not OK (status code other than 200)
            if (!response.ok) {
                throw new Error(`HTTP error! Status: ${response.status}`);
            }

            // Parse the JSON response body asynchronously
            const jsonData = await response.json();

            // Assign the fetched JSON data to the 'data' property
            this.data = jsonData;
        } catch (error) {
            // Handle errors that may occur during the HTTP request or JSON parsing
            this.error = error.message;
        }
    }
}

```

## Example 1: Asynchronous Fetch with await:

```
async function fetchUserData() {
  try {
    const response = await fetch('https://api.example.com/user');
    if (!response.ok) {
      throw new Error('HTTP Error: ' + response.status);
    }
    const userData = await response.json();
    console.log('User Data:', userData);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchUserData();
```


## Promices In JS:

In Salesforce Lightning Web Components (LWC), you can use Promises to handle asynchronous operations such as making server requests or interacting with external services. Here's a real-time example of using Promises in an LWC to make an asynchronous HTTP GET request to an external API and display the fetched data.

```
import { LightningElement, track } from 'lwc';

export default class PromiseExample extends LightningElement {
    @track error;
    @track data;

    connectedCallback() {
        this.fetchData()
            .then(result => {
                this.data = result;
            })
            .catch(error => {
                this.error = error;
            });
    }

    fetchData() {
        return new Promise((resolve, reject) => {
            fetch('https://jsonplaceholder.typicode.com/posts')
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`HTTP error! Status: ${response.status}`);
                    }
                    return response.json();
                })
                .then(data => {
                    resolve(data);
                })
                .catch(error => {
                    reject(error.message);
                });
        });
    }
}
```


```
// Function that returns a Promise, simulating an asynchronous operation
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulate an asynchronous operation (e.g., fetching data)
    setTimeout(() => {
      const success = true; // Simulate success (change to false to trigger an error)
      if (success) {
        resolve("Data is available!"); // Resolve the promise with a value
      } else {
        reject("Error occurred!"); // Reject the promise with an error message
      }
    }, 2000); // Simulate a 2-second delay
  });
}

// Async function to fetch and handle data
async function fetchAndHandleData() {
  try {
    const result = await fetchData(); // Try to fetch data
    console.log("Fulfilled:", result); // Log the successful result
  } catch (error) {
    console.error("Error:", error); // Handle any errors and log the error
  } finally {
    console.log("Finally block executed"); // Execute the finally block
  }
}

// Call the async function to initiate the process
fetchAndHandleData();
```

## Events in JS:

Standard Events:

Standard events are events that are predefined in LWC and can be used for common interactions. For example:

click: Triggered when an element is clicked.
change: Triggered when the value of an input element changes.
input: Triggered when the user interacts with an input element.
submit: Triggered when a form is submitted.
You can use standard events directly in your component's HTML template by specifying event attributes like onclick, onchange, etc.


<br/>

Event Types:

JavaScript supports various types of events, including but not limited to:

Mouse Events: click, mousedown, mouseup, mousemove, mouseover, mouseout, etc.
Keyboard Events: keydown, keyup, keypress
Form Events: submit, input, change, focus, blur
Document Events: load, unload, DOMContentLoaded, resize
Custom Events: You can create custom events using the CustomEvent constructor.


```
<button onclick={handleButtonClick}>Click Me</button>

// Access the data in the event handler
handleButtonClick(event) {
    const eventData = event.detail.data;
    // Use eventData as needed
```

```
import { LightningElement } from 'lwc';

export default class ParentComponent extends LightningElement {
    handleCustomEvent(event) {
        // Handle the custom event from the child component
        const message = event.detail.message;
        console.log('Custom Event Received: ', message);
    }
}
```

```
import { LightningElement } from 'lwc';

export default class MyComponent extends LightningElement {
    connectedCallback() {
        // This code is executed when the component is inserted into the DOM
        console.log('Component inserted into the DOM');
    }

    disconnectedCallback() {
        // This code is executed when the component is removed from the DOM
        console.log('Component removed from the DOM');
    }
}
```

## Event Handler:

1.  Adding an Event Listener for a Button Click
```
<template>
    <button id="myButton">Click Me</button>
</template>
```
```
import { LightningElement } from 'lwc';

export default class MyComponent extends LightningElement {
    connectedCallback() {
        // Get a reference to the button element
        const button = this.template.querySelector('#myButton');
        
        // Add a click event handler
        button.addEventListener('click', this.handleButtonClick.bind(this));
    }

    handleButtonClick() {
        // Handle the button click event here
        console.log('Button clicked');
    }
}
```


 2. Adding an Event Listener for a Custom Event
```
<template>
    <c-child-component></c-child-component>
</template>
```
```
import { LightningElement } from 'lwc';

export default class ParentComponent extends LightningElement {
    connectedCallback() {
        // Add an event listener for the custom event
        this.template.querySelector('c-child-component')
            .addEventListener('customclick', this.handleCustomEvent.bind(this));
    }

    handleCustomEvent(event) {
        // Handle the custom event from the child component
        const message = event.detail.message;
        console.log('Custom Event Received: ', message);
    }
}
```


## Custom Events In JS:

Child Component (childComponent.html)
```
<template>
    <lightning-button label="Send Custom Event" onclick={handleButtonClick}></lightning-button>
</template>
```
Child Component JavaScript (childComponent.js)
```
import { LightningElement } from 'lwc';

export default class ChildComponent extends LightningElement {
    handleButtonClick() {
        const event = new CustomEvent('customclick', {
            detail: { message: 'Hello from Child Component' }
        });
        this.dispatchEvent(event);
    }
}
```

Parent Component (parentComponent.html)
```
<template>
    <c-child-component oncustomclick={handleCustomEvent}></c-child-component>
    <p>{messageFromChild}</p>
</template>
```

```
import { LightningElement, track } from 'lwc';

export default class ParentComponent extends LightningElement {
    @track messageFromChild = '';

    handleCustomEvent(event) {
        this.messageFromChild = event.detail.message;
    }
}
```
