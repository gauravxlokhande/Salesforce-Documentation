## Disable any button if any input field is empty / u want a value from user forcefully

```
 handleSocietyFieldChange(event){
        this.field1 = event.target.value;
        this.disableBtn = !this.field1; // I will Disable the button if field1 is falsy (empty or null)

    }


.custom-box{
    transition: transform 0.3s ease-in-out;
}
.custom-box:hover{ 
         transform: scale(1.2);
}
```

```
 <lightning-button
    label="Click Me"          <!-- The text displayed on the button -->
    title="Hover over me"     <!-- The tooltip text when hovering over the button -->
    icon-name="utility:heart" <!-- The Lightning Design System (SLDS) icon to display next to the label -->
    icon-position="left"      <!-- The position of the icon relative to the label (left or right) -->
    variant="brand"           <!-- The style or variant of the button (brand, destructive, etc.) -->
    type="button"             <!-- The type of the button (button, reset, or submit) -->
    disabled                 <!-- Disables the button -->
    onclick={handleClick}     <!-- Event handler for button click -->
  ></lightning-button>
```



```
<lightning-input
  label="Input Label"            <!-- The label for the input field -->
  name="inputField"              <!-- The name attribute for the input field -->
  type="text"                    <!-- The type of input (text, password, etc.) -->
  value="Default Value"           <!-- The default value for the input field -->
  placeholder="Enter value"      <!-- The placeholder text for the input field -->
  required                       <!-- Indicates that the input field is required -->
  disabled                       <!-- Disables the input field -->
  readonly                       <!-- Makes the input field read-only -->
  maxlength="50"                 <!-- Maximum number of characters allowed -->
  minlength="5"                  <!-- Minimum number of characters required -->
  pattern="[A-Za-z0-9]*"         <!-- Regular expression pattern for validation -->
  message-when-bad-input="Invalid input format" <!-- Error message for bad input -->
  message-when-too-long="Input is too long"     <!-- Error message for input that is too long -->
  message-when-too-short="Input is too short"   <!-- Error message for input that is too short -->
  message-when-pattern-mismatch="Invalid input pattern" <!-- Error message for pattern mismatch -->
  message-when-value-missing="Input is required" <!-- Error message for missing required input -->
  onchange={handleInputChange}   <!-- Event handler for input changes -->
></lightning-input>

```

## Lightning Layout with layout item

<img width="464" alt="Screenshot 2023-12-15 104233" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/217f8b4d-ef48-4158-b1a8-6a2b77c69761">

```
 <template>
  <lightning-layout multiple-rows> <!-- Use the lightning-layout for the main layout -->
    <!-- Row 1 -->
    <lightning-layout-item size="12" padding="around-small">
      <!-- Use lightning-layout-item for individual layout items -->
      <p>Row 1, Full Width</p>
    </lightning-layout-item>

    <!-- Row 2 -->
    <lightning-layout-item size="6" small-size="12" padding="around-small">
      <!-- Use size and small-size to control column width at different screen sizes -->
      <p>Row 2, Half Width on Large Screen, Full Width on Small Screen</p>
    </lightning-layout-item>

    <lightning-layout-item size="6" small-size="12" padding="around-small">
      <p>Row 2, Half Width on Large Screen, Full Width on Small Screen</p>
    </lightning-layout-item>

    <!-- Row 3 -->
    <lightning-layout-item size="4" small-size="6" padding="around-small">
      <!-- Use padding to add space around the layout item -->
      <p>Row 3, One-Third Width on Large Screen, Half Width on Small Screen</p>
    </lightning-layout-item>

    <lightning-layout-item size="8" small-size="6" padding="around-small">
      <p>Row 3, Two-Thirds Width on Large Screen, Half Width on Small Screen</p>
    </lightning-layout-item>
  </lightning-layout>
</template>

```

## Iframe for show youtube video
<img width="309" alt="Screenshot 2023-12-15 104059" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/cf6150db-663f-4300-a3ea-1a8ccc9eb087">


```
<iframe 
  width="100%"                 <!-- Set the width of the iframe to 100% of its container -->
  height="100%"                <!-- Set the height of the iframe to 100% of its container -->
  src="https://www.youtube.com/embed/BmeFVjnALuQ?si=UhMj2RnZWobbsZAj"
                                <!-- Specify the URL of the content to be embedded (a YouTube video in this case) -->
  title="YouTube video player" <!-- Provide a title for the iframe, useful for accessibility -->
  frameborder="0"               <!-- Set the frameborder to 0 to remove the iframe border -->
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                                <!-- Allow specific permissions for the iframe content -->
  allowfullscreen              <!-- Allow the iframe to be displayed in full-screen mode -->
  sandbox="allow-same-origin allow-scripts allow-popups allow-forms"
                                <!-- Enable additional restrictions for added security -->
  loading="lazy"               <!-- Defer loading of the iframe until it's near the viewport -->
  name="myFrame"               <!-- Assign a name to the iframe (used as a target for hyperlinks or forms) -->
  referrerpolicy="no-referrer" <!-- Set the policy for handling the Referer header -->
  longdesc="https://example.com/description.html"
                                <!-- Provide a URL to a long description for accessibility -->
  marginwidth="0"               <!-- Set the margin width of the iframe (deprecated) -->
  marginheight="0"              <!-- Set the margin height of the iframe (deprecated) -->
  scrolling="no"               <!-- Specify whether or not to display scrollbars in the iframe (deprecated) -->
  seamless                     <!-- Suggest that the iframe should appear as part of the containing document -->
  allowpaymentrequest          <!-- Allow the iframe to make use of the Payment Request API -->
  loading="auto"               <!-- Use a more flexible loading strategy where the browser determines when to load -->
  importance="high"            <!-- Hint to the browser about the importance of the iframe content -->
></iframe>

```
## vertical scroll

```<img width="917" alt="Screenshot 2023-12-15 104431" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/cd2e5017-275a-4f86-af66-8849a273421f">

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

## Lwc Carosal for scrolling Image

<img width="382" alt="Screenshot 2023-12-15 103600" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/76bb5354-27ee-4d81-977e-c990b03ac68c">


```
   <lightning-carousel disable-auto-scroll>
            <lightning-carousel-image
                src={companyLogoUrl}
                header="Company logo"
                description="Company logo uploaded to a static resource"
                alternative-text="Company logo"
            >
            </lightning-carousel-image>
            <lightning-carousel-image
                src={product1Url}
                header="Fantastic product 1"
                description="Fantastic product image in a zip file"
                alternative-text="Fantastic product 1"
            >
            </lightning-carousel-image>
            <lightning-carousel-image
                src={product2Url}
                header="Fantastic product 2"
                description="Fantastic product image in a zip file"
                alternative-text="Fantastic product 2"
            >
            </lightning-carousel-image>
        </lightning-carousel>
```

## refer for login Functionality
```
https://youtu.be/HXJXUFeWmMg?si=VoESxMud-rkOAq-M
```

## lwc menu
<img width="938" alt="Screenshot 2023-12-15 154543" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/d619d08b-8153-4b81-9d75-187e4c88db11">

<img width="99" alt="Screenshot 2023-12-15 154553" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/218586ca-1373-47ed-9ff5-5561a4c03fbe">


```
 <lightning-menu-item 
        value={menuItemValue} 
        label={menuItemLabel}
        onmouseover={handleMouseOver}
        onmouseleave={handleMouseLeave}
        onclick={handleClick}>
    </lightning-menu-item>
```
```
    <lightning-button-menu alternative-text="Show menu" icon-name="utility:down" icon-size="xx-small" label=""
        onclick={clickHandler} variant="bare">
        <lightning-menu-item value="menuItemOne" label="Menu Item One"></lightning-menu-item>
             <lightning-menu-divider></lightning-menu-divider> // it forms a line to divide above menue from below
        <lightning-menu-item value="menuItemTwo" label="Menu Item Two"></lightning-menu-item>
        <lightning-menu-item value="menuItemThree" label="Menu Item Three"></lightning-menu-item>
    </lightning-button-menu>
```
