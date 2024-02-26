## loadcustomecss.HTML
```
<template>
        <h1 class="slds-text-heading_large animate__bounceIn animate__delay-4s">CheckInn</h1>
</template>
```

## loadcustomecss.HTML
```
// aboutcheckinn.js
import { LightningElement, track } from 'lwc';
import thirdpartycss from '@salesforce/resourceUrl/thirdpartycss';
import { loadStyle } from 'lightning/platformResourceLoader';

export default class Aboutcheckinn extends LightningElement {

    @track FirstLoad = true;

    renderedCallback() {
       if (this.FirstLoad) {
           loadStyle(this, thirdpartycss)
               .then((result) => {
                   console.log('CSS loaded successfully');
                   this.FirstLoad = false;
               })
               .catch((error) => {
                   console.error('Error loading CSS: ', error);
               });
       }
    }
}

```


# for js and Html both

```
// aboutcheckinn.js
import { LightningElement, track } from 'lwc';
import thirdpartycss from '@salesforce/resourceUrl/bootstrap';
import bootstrapjs from '@salesforce/resourceUrl/bootstrapjs';
import { loadStyle, loadScript } from 'lightning/platformResourceLoader';

export default class Aboutcheckinn extends LightningElement {

    @track FirstLoad = true;

    renderedCallback() {
        if (this.FirstLoad) {
            Promise.all([
                loadStyle(this, thirdpartycss),
                loadScript(this, bootstrapjs)
            ]).then(() => {
                console.log('CSS and JS loaded successfully');
                this.FirstLoad = false;
            }).catch(error => {
                console.error('Error loading resources: ', error);
            });
        }
    }
}


```
