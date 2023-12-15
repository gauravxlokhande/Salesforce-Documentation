## Disable any button if any input field is empty / u want a value from user forcefully

```
 handleSocietyFieldChange(event){
        this.field1 = event.target.value;
        this.disableBtn = !this.field1; // I will Disable the button if field1 is falsy (empty or null)

    }
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
