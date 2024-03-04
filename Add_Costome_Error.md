
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
