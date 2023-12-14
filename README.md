## Disable any button if any input field is empty / u want a value from user forcefully

```
 handleSocietyFieldChange(event){
        this.field1 = event.target.value;
        this.disableBtn = !this.field1; // I will Disable the button if field1 is falsy (empty or null)

    }
```

```
<lightning-input 
    id='firstName'
    data-key="firstName"
    type="text" 
    autocomplete="off"
    max-length ="15"
    label="First name"
    value={firstName}
    onchange={handleInput}
    class="firstNameCls"
    message-when-value-missing="Required input"
    required></lightning-input>
```

```
    <lightning-layout>
        <lightning-layout-item padding="around-small">
            <div class="custom-box slds-box slds-p-around_medium slds-text-align_center">1</div>
        </lightning-layout-item>
        <lightning-layout-item padding="around-small">
            <div class="custom-box slds-box slds-p-around_medium slds-text-align_center">2</div>
        </lightning-layout-item>
        <lightning-layout-item padding="around-small">
            <div class="custom-box slds-box slds-p-around_medium slds-text-align_center">3</div>
        </lightning-layout-item>
        <lightning-layout-item padding="around-small">
            <div class="custom-box slds-box slds-p-around_medium slds-text-align_center">4</div>
        </lightning-layout-item>
    </lightning-layout>
```

```
 <div class="slds-nav-vertical__section">
        <ul>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action" href="https://www.w3web.net/"
                    target="_blank" rel="noopener noreferrer">w3web Tutorial</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/salesforce-integration/" target="_blank"
                    rel="noopener noreferrer">Salesforce Integration</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/salesforce-lwc/" target="_blank"
                    rel="noopener noreferrer">Salesforce LWC</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/lightning-component/" target="_blank"
                    rel="noopener noreferrer">Salesforce Aura Component</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/trigger/" target="_blank" rel="noopener noreferrer">Apex
                    Trigger</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/visualforce/" target="_blank"
                    rel="noopener noreferrer">Visualforce</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/tutorial/jquery/" target="_blank"
                    rel="noopener noreferrer">JQuery/Javascript</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/all-published-post/" target="_blank" rel="noopener noreferrer">Sitemap
                    W3web</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/about-us/" target="_blank" rel="noopener noreferrer">About Us</a></li>
            <li class="slds-nav-vertical__item"><a class="slds-nav-vertical__action"
                    href="https://www.w3web.net/contact-us/" target="_blank" rel="noopener noreferrer">Contact Us</a>
            </li>
        </ul>
    </div>

```
