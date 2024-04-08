# Pass Input to Apex Method Efficiently.md

## myclass.apex
```
public class MyClass {
    public class MyCustomObject {
        @AuraEnabled
        public String name;
        @AuraEnabled
        public Integer age;
        @AuraEnabled
        public Boolean active;
    }
    
    @AuraEnabled
    public static void processData(MyCustomObject obj) {
        // Create a new Contact instance
        Contact con = new Contact();
        // Set the name field of the Contact using the value from MyCustomObject
        con.Name = obj.name;
        // Optionally, perform additional processing or operations here
    }
}
```

## myclass.js
```
import { LightningElement } from 'lwc';
import processData from '@salesforce/apex/MyClass.processData';

export default class MyComponent extends LightningElement {
    // Define the data to be passed to the Apex method
    data = {
        name: 'John Doe',
        age: 30,
        active: true
    };

    // Method to handle button click event
    handleClick() {
        // Call the Apex method imperatively
        processData({ obj: this.data })
            .then(result => {
                // Handle the result if needed
                console.log('Apex method processData executed successfully:', result);
            })
            .catch(error => {
                // Handle any errors that occur during the Apex method execution
                console.error('Error executing Apex method processData:', error);
            });
    }
}

```
