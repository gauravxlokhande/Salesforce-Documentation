
<img width="398" alt="Screenshot 2023-09-27 174024" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/0ba6c84d-7551-44af-888e-5b06ea788be3">


## Create a Child Component:

First, create a child component that will emit a custom event. For example, let's create a simple child component named childComponent.

```
<!-- childComponent.html -->
<template>
    <button onclick={notifyParent}>Notify Parent</button>
</template>
```

```
// childComponent.js
import { LightningElement } from 'lwc';

export default class ChildComponent extends LightningElement {
    notifyParent() {
        // Create a custom event and dispatch it to notify the parent component
        const event = new CustomEvent('notify');
        this.dispatchEvent(event);
    }
}
```

## Create a Parent Component:

Next, create a parent component that will include the child component and handle the custom event.

```
<!-- parentComponent.html -->
<template>
    <c-child-component onnotify={handleNotify}></c-child-component>
    <p>Notification from child: {messageFromChild}</p>
</template>
```

```
// parentComponent.js
import { LightningElement, track } from 'lwc';

export default class ParentComponent extends LightningElement {
    @track messageFromChild = '';

    handleNotify(event) {
        // Handle the custom event triggered by the child component
        this.messageFromChild = 'Child component notified the parent.';
    }
}
```


# Parent to child:

SCENARIO: i want to sent the id that i getting from the record edit form field and i wnat to send it to event page for gave to the method so that it can return me the perticular records that i want.


Societymodalscreen.js

```
 @track modalscreenforevents = true;

    @api eventid;
    onclickofsave() {
        let inputField = this.template.querySelector('[data-id="society"]');
        this.eventid = inputField.value;    

        this.dispatchEvent(new CustomEvent('passid', { detail: this.eventid }));
         this.modalscreenforevents = false;   
     

    }
```

Societymodalscreen.html

```

                    <lightning-record-edit-form density="compact" object-api-name="Event__c">

                        <lightning-input-field field-name="Society__c" data-id="society" variant="standard">
                        </lightning-input-field>

                        <div class="savebtn">
                            <lightning-button variant="brand" type="submit" label="Save" onclick={onclickofsave}
                                class="slds-var-p-around_medium">
                            </lightning-button>
                        </div>


                    </lightning-record-edit-form>
```

```
 <template if:true={eventspage}>
        <c-events-page>
            StoreEventID={eventid}
        </c-events-page>
    </template>
```

eventpage.html

```
<template if:true={modalscreen}>
        <c-select-society-name-modal-screen onpassid={handlePassId}></c-select-society-name-modal-screen>
    </template>
```


eventpage.js

```
 eventid;

    handlePassId(event) {
        this.eventid = event.detail;
    }

```


## querySelector in an LWC:

```
<!-- querySelectorExample.html -->
<template>
    <div>
        <p class="message">Hello, World!</p>
        <button onclick={changeText}>Change Text</button>
    </div>
</template>
```

```
// querySelectorExample.js
import { LightningElement } from 'lwc';

export default class QuerySelectorExample extends LightningElement {
    changeText() {
        // Use querySelector to select the <p> element with the class "message"
        const paragraph = this.template.querySelector('.message');

        // Check if the element is found
        if (paragraph) {
            // Change the text content of the selected element
            paragraph.textContent = 'Text Changed!';
        }
    }
}
```
