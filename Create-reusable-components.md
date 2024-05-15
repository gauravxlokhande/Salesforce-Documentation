## Card.html
```
<template>
    <!-- First Modal -->
    <template if:true={hideModal}>
        <c-modal 
            title="Gaurav" 
            body="Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ducimus aut delectus odio exercitationem, rerum nisi officia sint cumque. Rem autem iste quisquam iusto officiis porro ad doloribus! Necessitatibus, commodi quaerat!"
            has-header-string={hide}>
            
            <!-- Custom footer buttons -->
            <div class="slds-align_absolute-center" slot="buttons">
                <lightning-button variant="brand" label="Button Label" onclick={handleClickclose}></lightning-button>
                <lightning-button variant="brand" label="Button Label" onclick={handleClick}></lightning-button>
            </div>
        </c-modal>
    </template>

    <!-- Second Modal -->
    <template if:true={hidemodaltwo}>
        <c-modal 
            title="Atharva" 
            onclosebutton={handleCloseButton} 
            has-header-string={hide2}
            body="cimus aut delectus odio exercitationem, rerum nisi officia sint cumque. Rem autem iste quisquam iusto officiis porro ad doloribus! Necessitatibus, commodi quaerat!">
            
            <!-- Custom header content -->
            <div slot="header">
                <h1>Testing component</h1>
            </div>
        </c-modal>
    </template>
</template>

```


## Card.js
```
import { LightningElement, track } from 'lwc';

export default class Card extends LightningElement {
    @track hideModal = true; // Track the visibility of the first modal
    @track hidemodaltwo = false; // Track the visibility of the second modal
    @track hide = true; // Determine the header type for the first modal
    @track hide2 = false; // Determine the header type for the second modal

    handleClickclose() {
        this.hideModal = false; // Close the first modal
        this.hidemodaltwo = true; // Open the second modal
    }

    handleCloseButton(event) {
        this.hidemodaltwo = false; // Close the second modal
    }
}

```

## Modal.html
```
<template>
    <section role="dialog" tabindex="-1" aria-modal="true" aria-labelledby="modal-heading-01"
        class="slds-modal slds-fade-in-open">
        <div class="slds-modal__container">
            <!-- Close button -->
            <button class="slds-button slds-button_icon slds-modal__close slds-button_icon-inverse" onclick={handleCloseClick}>
                <lightning-icon icon-name="utility:close" alternative-text="close" size="small" title="close"></lightning-icon>
            </button>
            <div class="slds-modal__header">
                <!-- Conditionally render header based on hasHeaderString property -->
                <template if:true={hasHeaderString}>
                    <h2 class="slds-text-heading_medium slds-hyphenate header-string">
                        {title}
                    </h2>
                </template>
                <template if:false={hasHeaderString}>
                    <h2 class="slds-text-heading_medium slds-hyphenate header-slot">
                        <slot name="header"></slot>
                    </h2>
                </template>
            </div>
            <div class="slds-text-align_center slds-modal__content slds-p-around_medium" id="modal-content-id-1">
                {body}
            </div>
            <div class="slds-modal__footer">
                <!-- Slot for custom footer buttons -->
                <slot name="buttons">
                    <button class="slds-button slds-button_neutral" aria-label="Cancel and close" onclick={handleCloseClick}>Cancel</button>
                    <button class="slds-button slds-button_brand">Save</button>
                </slot>
            </div>
        </div>
    </section>
    <div class="slds-backdrop slds-backdrop_open" role="presentation"></div>
</template>

```

## Modal.js
```
import { LightningElement, api } from 'lwc';

export default class Modal extends LightningElement {
    @api title = ''; // Title of the modal
    @api body = ''; // Body content of the modal
    @api hasHeaderString = false; // Flag to determine if header is a string or custom slot

    handleCloseClick() {
        // Dispatch a custom event to signal the close button was clicked
        const event = new CustomEvent('closebutton');
        this.dispatchEvent(event);
    }
}

```
