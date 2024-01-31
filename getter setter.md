# getter setter example in js:


gettersetter.html
```
<template>
    <lightning-card icon-name="standard:account" variant="base">
        <lightning-input type="text" label="Enter some text" onchange={onchangofage} value={agevalue}></lightning-input>
        <h1>{itemName}</h1>
    </lightning-card>
</template>

```



gettersetter.js
```
import { LightningElement, track } from 'lwc';

export default class Testall extends LightningElement {

  @track newage;

  get itemName() {
    return this.newage;
  }
  set itemName(value) {
    this.newage = value;
  }

  onchangofage(event) {
    const agevalue = event.target.value;
    this.itemName = agevalue;
  }   
}
```





