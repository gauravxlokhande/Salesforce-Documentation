## Disable any button if any input field is empty / u want a value from user forcefully

```
 handleSocietyFieldChange(event){
        this.field1 = event.target.value;
        this.disableBtn = !this.field1; // I will Disable the button if field1 is falsy (empty or null)

    }
```

