# getter setter example in js:


gettersetter.html
```
<template>
    <lightning-card icon-name="standard:account" variant="base">
        <lightning-input type="text" label="Enter some text" onchange={onchangofage} value={agevalue}></lightning-input>
        <h1>{itemName}</h1>  // getter name because it returning the value.
    </lightning-card>
</template>

```



gettersetter.js
```
import { LightningElement, track } from 'lwc';

export default class Testall extends LightningElement {

  @track newage;

  get itemName() {
    return this.newage; // here we return the value of variable so it accicable in html
  }
  set itemName(value) {
    this.newage = value;   // hetre we set the value in variable
  }

  onchangofage(event) {
    const agevalue = event.target.value;
    this.itemName = agevalue;   // by assigning value to setter name we can assign value
  }   
}
```





