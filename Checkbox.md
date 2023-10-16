## checkbox

```
 <lightning-input type="checkbox" checked={CheckboxValue}
                            onchange={oncheckboxchange}></lightning-input>
```

```
 oncheckboxchange(event) {
        this.CheckboxValue = event.target.Checked;
    }
```

```
  onSelectAllButton() {
        this.CheckboxValue = true;
    }
    ondblclickonSelectAllButton(){
         this.CheckboxValue = false;
    }
```
