
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
