
## the scenarion is we need to put the validation on the input field description if it is empty and user press submit button.

```
<lightning-textarea name="Description" placeholder="Share your query..." value={queryValue}
onchange={handleQueryChange} variant="standard" class="text-area"></lightning-textarea>

<lightning-button style="display: flex;justify-content:center" variant="brand" label="Submit"
onclick={handleSubmitClick}></lightning-button>
```

## when value is enpty or non empty validation on  button.

```
 handleQueryChange(event){
        this.queryValue = event.target.value;
    }
    handleSubmitClick(){
        console.log('enter')
        let isValid = true;
        this.template.querySelectorAll("lightning-textarea").forEach(item=>{
            let fieldValue = item.value;
            let fieldName = item.name;

            let fieldError = 'Please Enter the';
            if(!fieldValue){
                isValid = false;
                item.setCustomValidity(fieldError +" "+ fieldName);
            }else{
                item.setCustomValidity("");
            }
            item.reportValidity();
        });
        if(!isValid){
            return;
        }
        insertFeedback({queryValue:this.queryValue})
        .then(result=>{
            console.log('result',result);
            this.dispatchEvent(new ShowToastEvent({
                title: "Record Submitted Succesfully...",
                variant: "success"
            }));
            this.queryValue = '';
        })
        .catch(error=>{
            console.log('error',error);
        })

    }
```
