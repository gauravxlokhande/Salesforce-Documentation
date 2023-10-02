```
<template>
    <lightning-card>

        <div class="test">
            <div class="input">
                <lightning-input type="text" label="Enter some text" onchange={handleinput}
                    value={storetext}></lightning-input>
            </div>
            <div class="button">
                <lightning-button variant="base" label="Button Label" onclick={handleButtonClick}></lightning-button>
            </div>
        </div>

        <template if:true={StoreData}>
            <template for:each={StoreData} for:item="acc">
                <option key={acc.id}>
                    {acc.Name}
                </option>
            </template>
        </template>

    </lightning-card>


</template>
```

```
import { LightningElement, track, wire } from 'lwc';
import Account_data from '@salesforce/apex/AccountSearch.SearchInAccountData';

export default class FirstPage extends LightningElement {

    @track holdinputdata = '';

    @track StoreData = [];

    @track error = '';

    handleinput() {
        const holdinputdata = event.target.value;
    }

   async handleButtonClick() {
        try {
            this.StoreData = await Account_data({ SearchData: this.holdinputdata });
            this.error = undefined; // Clear any previous errors
        } catch (error) {
            this.error = error; // Handle and track errors
            this.StoreData = []; // Clear the data in case of an error
        }
    }


//-------------------------------------------------------------------------------------



    @track AccountData = ''; //var

    @track StoreData = [];  //data

    @track storetext = '';   


    @wire(Account_data, { SearchData:'$AccountData' })
    Account_data ({error, data}) {
        if (data) {
            this.StoreData = data;
        } else if (error) {
            this.StoreData = undefined; 
        }
    }

    handleinput(event) {
        this.storetext = event.target.value;
    }

    handleButtonClick(event) {
        this.AccountData = event.target.value;
        this.AccountData = this.storetext;
        
    
    }


}
```


```

public with sharing class AccountSearch {

    
    @AuraEnabled(Cacheable=true)
    public static List<Account> SearchInAccountData(String SearchData){
            String KeyString = '%'+SearchData+'%';
        return[Select Id,Name From Account where Name Like: KeyString];
    }
}


```
