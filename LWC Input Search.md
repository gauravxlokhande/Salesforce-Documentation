# LWC-JS-Cheetsheet

# HTML:
```
<template>
    <lightning-card title="Contact Data">
        <lightning-input type="text" label="Enter some text" onchange={onvaluechange}></lightning-input>
        <template for:each={storedata} for:item="sorteddata" for:index="index">
            <option key={sorteddata.id}>{sorteddata.Name}</option>
        </template>
    </lightning-card>
</template>
```

# JS:
```
import { LightningElement, track, wire } from 'lwc';
import searchbyname from'@salesforce/apex/searchonaccountname.searchbyname'

export default class CaseHierarchyComponent extends LightningElement { 
    accountname = '';
    storedata = [];
    @wire(searchbyname, { searchinit: '$accountname' })
    isdataget({ data, error }) {
        if (data) {
            this.storedata = data;
        }else if (error) {
            this.storedata = undefined;
        }   
    }
    onvaluechange(event) {
        this.accountname = event.target.value;
    }
}
```
# LWC Apex:
```
public with sharing class searchonaccountname {
      @AuraEnabled(cacheable=true)
    public static List<Account> searchbyname(String searchinit){
         String keystring ='%'+searchinit+'%';
        return [Select id, Name from Account where Name Like :keystring ];           
    }
}
```


# Output:


<img width="939" alt="Screenshot 2023-09-21 163621" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/ff9f7c8d-7ba9-4dab-8938-4008c9e80c5d">
