# Salesforce Extensions chrome an vs code

```
Salesforce Assistant

Salesforce Lightning Grid System

Salesforce LWC Short Keys

```
# Query selector & queryselector all using .class

```
 <div>
        <lightning-input type="text" name="id1" class="gaurav" label="Enter some text"></lightning-input>
        <lightning-input type="text" name="id1" class="gaurav" label="Enter some text"></lightning-input>
        <lightning-input type="text" name="id1" class="gaurav" label="Enter some text"></lightning-input>
        <lightning-input type="text" name="id1" class="gaurav" label="Enter some text"></lightning-input>

        <lightning-button variant="base" label="Button Label" onclick={handleClick}></lightning-button>
    </div>
```

```
handleClick() {
        // Query all elements with class 'gaurav'
        let storedata = this.template.querySelectorAll('.gaurav'); // for selecting class always use .gaurav like dot and classname.

        // Convert NodeList to an array and iterate over each element
        const dataArray = Array.from(storedata);
        dataArray.forEach((item) => {
            if (item.value =='gaurav') {
                alert('gauravcalled')
            } else {
                console.log(item.value);
            }
         
        });
    }
```

# queryselector and queryselectorall using dataid

```
 <lightning-input type="text" data-id="example-input-1" label="Enter some text"></lightning-input>
 <lightning-button variant="base" label="Get Input Value" onclick={handleClick}></lightning-button>
```

```
handleClick() {
        // Query the input element by data-id attribute
        const inputElement = this.template.querySelector('[data-id="example-input-1"]'); // by using data id use [data-id="example-input-1"] like this always 

        // Check if the input element is found
        if (inputElement) {
            // Log the value of the input field
            console.log('Input Value:', inputElement.value);
        } else {
            console.error('Input element not found.');
        }
    }
```
