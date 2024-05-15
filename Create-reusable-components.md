## Card.html
```
<template>
    <template if:true={hideModal}>
        <c-modal title="Gaurav" body='Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ducimus aut delectus odio exercitationem, rerum nisi officia sint cumque. Rem autem iste quisquam iusto officiis porro ad doloribus! Necessitatibus, commodi quaerat!
        '>
            <div class="slds-align_absolute-center" slot="buttons">
                <div>
                    <lightning-button variant="brand" label="Button Label"
                        onclick={handleClickclose}></lightning-button>
                </div>
                <div>
                    <lightning-button variant="brand" label="Button Label" onclick={handleClick}></lightning-button>
                </div>
            </div>
        </c-modal>
    </template>

    <template if:true={hidemodaltwo}>
        <c-modal title="Atharva" onclosebutton={handleCloseButton}
            body='cimus aut delectus odio exercitationem, rerum nisi officia sint cumque. Rem autem iste quisquam iusto officiis porro ad doloribus! Necessitatibus, commodi quaerat!'>
        </c-modal>
    </template>

</template>
```


## Card.js
```
import { LightningElement, track } from 'lwc';

export default class Card extends LightningElement {
    @track hideModal = true;
    @track hidemodaltwo = false;
    

    handleClickclose() {
        this.hideModal = false;
        this.hidemodaltwo = true;
    }
    handleCloseButton(event) {
        this.hidemodaltwo = false;
    }
}
```

## Modal.html
```
<template>
    <section role="dialog" tabindex="-1" aria-modal="true" aria-labelledby="modal-heading-01"
        class="slds-modal slds-fade-in-open">
        <div class="slds-modal__container">
            <button class="slds-button slds-button_icon slds-modal__close slds-button_icon-inverse">
                <lightning-icon icon-name='utility:close' alternative-text='close' size='small'
                    title='close'></lightning-icon>
            </button>
            <div class="slds-modal__header">
                <h1 id="modal-heading-01" class="slds-modal__title slds-hyphenate">{title}</h1>
            </div>
            <div class=" slds-text-align_center slds-modal__content slds-p-around_medium" id="modal-content-id-1">
                {body}
            </div>
            <div class="slds-modal__footer">
                <slot name="buttons">
                    <button class="slds-button slds-button_neutral" aria-label="Cancel and close"
                        onclick={handleCloseClick}>Cancel</button>
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

    @api title = '';
    @api body = '';

    
    handleCloseClick() {
        const event = new CustomEvent('closebutton');
        this.dispatchEvent(event);
    }
}
```
