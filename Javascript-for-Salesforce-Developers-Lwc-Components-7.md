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


# Promices In JS:

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
