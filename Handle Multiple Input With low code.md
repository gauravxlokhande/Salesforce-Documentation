```
import { LightningElement, wire } from 'lwc';
import processData from '@salesforce/apex/MyClass.processData';

export default class MyComponent extends LightningElement {
    // Define properties to hold input values
    name = '';
    age = 0;
    active = false;

    // Method to handle input changes
    handleInputChange(event) {
        // Update respective property based on input field name
        const { name, value } = event.target;
        if (name === 'name') {
            this.name = value;
        } else if (name === 'age') {
            this.age = parseInt(value, 10); // Convert string to integer
        } else if (name === 'active') {
            this.active = event.target.checked;
        }
    }

}

```
