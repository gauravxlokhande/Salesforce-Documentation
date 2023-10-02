HTML:

```
     <template if:true={StoreData}>
            <template for:each={StoreData} for:item="acc">
                <option data-record-id={acc.id} key={acc.id}>
                    {acc.Name}
                </option>
            </template>
        </template>
```

JS:
```
  onnavigate(event) {
        const recordid =event.currentTarget.dataset.value

         this[NavigationMixin.Navigate]({
        type: "standard__recordPage",
        attributes: {
            actionName: "navigate",
            recordId: recordId,
            objectApiName: "Account"
        }
    });
    }
```