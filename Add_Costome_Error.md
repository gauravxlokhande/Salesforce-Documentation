
![image](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/029d8ff6-db94-49cc-9d35-790f8be911bc)


## CustomeError.html
```
<template>
    <lightning-card title="Custom Validations In Lightning Web Components">
        <lightning-input class="nameCmp" label="Enter Name" type="string"></lightning-input>
        <lightning-input class="dateCmp" label="Enter Date" type="date"></lightning-input><br /><br />
        <lightning-button class="slds-align_absolute-center" label="Search" variant="brand"
            onclick={searchTheData}></lightning-button>
    </lightning-card>
</template>
```

## CustomeError.Js
```
 searchTheData() {
        let searchCmp = this.template.querySelector(".nameCmp");
        let dateCmp = this.template.querySelector(".dateCmp");
        let searchvalue = searchCmp.value;
        let dtValue = dateCmp.value;
        console.log(dtValue)
       
        if (!searchvalue) {
            searchCmp.setCustomValidity("Name value is required");
        } else{
            searchCmp.setCustomValidity(""); // clear previous value
        }
        searchCmp.reportValidity();

        if (!dtValue) {
            dateCmp.setCustomValidity("Date value is required");
        } else {
            dateCmp.setCustomValidity(""); // clear previous value
        }
        dateCmp.reportValidity();
    }
```




component2.html

```
<template>
  <lightning-input
    label="Name"
    value={name}
    onchange={handleNameChange}
    required
  ></lightning-input>
  <div class="error">{nameError}</div>

  <lightning-input
    label="Email"
    value={email}
    onchange={handleEmailChange}
    pattern=".+@.+\..+"
    required
  ></lightning-input>
  <div class="error">{emailError}</div>

  <lightning-button label="Submit" onclick={handleSubmit} variant="brand"></lightning-button>
</template>
```
component2.js
```
import { LightningElement, track } from 'lwc';

export default class FormValidationExample extends LightningElement {
  @track name = '';
  @track email = '';
  @track nameError = '';
  @track emailError = '';

  handleNameChange(event) {
    this.name = event.target.value;
  }

  handleEmailChange(event) {
    this.email = event.target.value;
  }

  handleSubmit() {
    // Validate Name
    if (!this.name) {
      this.nameError = 'Name is required.';
    } else {
      this.nameError = '';
    }

    // Validate Email
    if (!this.email) {
      this.emailError = 'Email is required.';
    } else if (!this.email.match('.+@.+\..+')) {
      this.emailError = 'Please enter a valid email address.';
    } else {
      this.emailError = '';
    }

    // Submit form if there are no errors
    if (!this.nameError && !this.emailError) {
      // Perform form submission logic
      // ...
    }
  }
}
```

component3.html
```
<template>
  <lightning-input
    label="Password"
    type="password"
    value={password}
    onchange={handlePasswordChange}
    required
  ></lightning-input>
  <div class="error">{passwordError}</div>

  <lightning-button
    label="Submit"
    onclick={handleSubmit}
    variant="brand"
  ></lightning-button>
</template>
```
component3.js
```
import { LightningElement, track } from 'lwc';

export default class PasswordValidationExample extends LightningElement {
  @track password = '';
  @track passwordError = '';

  handlePasswordChange(event) {
    this.password = event.target.value;
    this.validatePassword();
  }

  validatePassword() {
    if (!this.password) {
      this.passwordError = 'Password is required.';
    } else if (this.password.length < 8) {
      this.passwordError = 'Password should be at least 8 characters long.';
    } else if (!/[A-Z]/.test(this.password)) {
      this.passwordError = 'Password should contain at least one uppercase letter.';
    } else if (!/[0-9]/.test(this.password)) {
      this.passwordError = 'Password should contain at least one numeric digit.';
    } else {
      this.passwordError = '';
    }
  }

  handleSubmit() {
    if (!this.passwordError) {
      // Form is valid, perform submission logic
      // ...
    }
  }
}
```

# To refer validatios more advance refer:

```
https://sfdclesson.com/2023/07/05/enhancing-form-validation-in-lightning-web-components-lwc/
```
