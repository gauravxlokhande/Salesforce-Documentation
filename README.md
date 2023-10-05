# Different Ways to fetch data from Wire


## only fetch data
```
import { LightningElement, wire } from 'lwc';
import getAccountList from '@salesforce/apex/AccountController.getAccountList';

export default class AccountList extends LightningElement {
    @wire(getAccountList) accounts;
}
```
## gave data to parameter and fetch data

```
import { LightningElement, wire } from 'lwc';
import getContactsByAccountId from '@salesforce/apex/ContactController.getContactsByAccountId';

export default class ContactList extends LightningElement {
    accountId = '0012w00000XYZabcde'; // Example Account Id

    @wire(getContactsByAccountId, { accountId: '$accountId' }) contacts;
}
```

## syntax to get data

```
@wire(getAccountList)
wiredAccounts({ data, error }) {
    if (data) {
        // Process data
    } else if (error) {
        // Handle error
    }
}
```

## refresh data
```
@wire(getAccountList)
accounts;

refreshData() {
    this.accounts.refresh();
}
```


## get any object data by not calling any any apex method

```
<!-- HTML File - accountList.html -->
<template>
    <lightning-card title="Account List">
        <template if:true="{accountList}">
            <ul>
                <template for:each="{accountList}" for:item="account">
                    <li key="{account.id}">{account.fields.Name.value}</li>
                </template>
            </ul>
        </template>
    </lightning-card>
</template>

```

```
// JS File - accountList.js
import { LightningElement, wire } from 'lwc';
import { getListUi } from 'lightning/uiListApi';
import ACCOUNT_OBJECT from '@salesforce/schema/Account';
 
export default class AccountList extends LightningElement {
    @wire(getListUi, { objectApiName: ACCOUNT_OBJECT, listViewApiName: 'AllAccounts' })
    accounts;
 
    get accountList() {
        return this.accounts.data ? this.accounts.data.records.records : [];
    }
}

```

## on buttonclick get data

```
<template>
    <div>
        <lightning-button label="Fetch Data" onclick={handleClick}></lightning-button>
        <ul>
            <template for:each={data} for:item="item">
                <li key={item.Id}>{item.Name}</li>
            </template>
        </ul>
    </div>
</template>
```


```
import { LightningElement } from 'lwc';
import getApexData from '@salesforce/apex/getaccountdatataa.getlistofacc';

export default class Testttttttttt extends LightningElement {
    data = [];

    gauravg() {
        getApexData()
            .then(result => {
                // Handle the successful response
                this.data = result;
            })
            .catch(error => {
                // Handle any errors that occur
                console.error('Error fetching data: ', error);
            });
    }

    handleClick() {
        this.gauravg(); // Call the Apex method when a button is clicked
    }
}
```

