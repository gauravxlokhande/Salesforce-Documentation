
## Parent To Child:
```
<c-lwc>
 onSubtract{handledecrement}
</c-lwc>


handlesubtract(){
this.dispatchEvent(new customeEvent('Subtract'));
}
```

## Events In Lwc:
```
lwcbtn:
 <button || data-name="Button 1"|| onclick={handleButtonClick}>Button 1</button>

handleButtonClick(event) {
        const buttonName = event.currentTarget.dataset.name;
        console.log(`Clicked on ${buttonName}`);
    }

handleButtonClick(event) {
        const buttonName = event.target.value;
        console.log(`Clicked on ${buttonName}`);
    }

```
----------------------------------------------
## child to parent query:
```
List<Contact> conlist =[Select Id, Firstname , Account.Name from Contact];

Parent To Child Query:

List<Account> accList =[Select Id , Name,(Select LastName) from Account];

```
