
<img width="298" alt="Screenshot 2023-10-18 110843" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/826ecfd9-16f7-4a24-b888-8098930ce002">

<img width="293" alt="Screenshot 2023-10-18 112136" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/0529cb1a-090a-44f0-9463-50d762d8b298">




## Filter For CheckBox:
## HTML:
```
div class="container">

<lightning-tabset variant="vertical">
                    <lightning-tab label="Category">
                        <lightning-input type="checkbox" label="New Business" onchange={handleCheckboxChange}
                            checked={NewBusinessCheckBox}></lightning-input>

                        <lightning-input type="checkbox" label="Existing Customer" onchange={handleCheckboxChange}
                            checked={ExistingCustomerCheckbox}></lightning-input>

                        <lightning-input type="checkbox" label="Partner Referral" checked={Partnerreferralcheckbox}
                            onchange={handleCheckboxChange}></lightning-input>

                        <lightning-input type="checkbox" label="Marketing Campaign"
                            checked={oncheckedMarketingCampaign}></lightning-input>
                        <lightning-input type="checkbox" label="Employee Referral"
                            checked={oncheckedEmployeeReferral}></lightning-input>
                        <lightning-input type="checkbox" label="Other" onclick={oncheckedOther}></lightning-input>
                    </lightning-tab>
</lightning-tabset>

        div class="buttonsscreenthree">
             <lightning-button variant="base" label="Reset" onclick={onClickResetButton}></lightning-button>
            <lightning-button variant="brand" label="Filter" onclick={onClickFilterButton}></lightning-button>
     </div>

</div>
```


## JS:


```

 handleCheckboxChange(event) {
        const checkboxName = event.target.label;
        const isChecked = event.target.checked;
        this.checkboxName = checkboxName;
        this.isChecked = isChecked;
    }

    onClickFilterButton() {
        this.FilterScreenThree = false;
        this.ShowDetaisOfCreatedRecords = true;

        if (this.checkboxName === 'New Business') {
            this.NewBusinessCheckBox = this.isChecked;
            this.searchbarvalue = 'New Business';
            this.OnSearchInLeadData();
            this.NewBusinessCheckBox = false;
            this.searchbarvalue = null;
        } else if (this.checkboxName === 'Existing Customer') {
            this.ExistingCustomerCheckbox = this.isChecked;
            this.searchbarvalue = 'Existing Customer';
            this.OnSearchInLeadData();
            this.searchbarvalue = null;
            this.ExistingCustomerCheckbox = false;
        } else if (this.checkboxName === 'Partner Referral') {
            this.Partnerreferralcheckbox = this.isChecked;
            this.searchbarvalue = 'Partner Referral';
            this.OnSearchInLeadData();
            this.Partnerreferralcheckbox = false;
            this.searchbarvalue = null;
        }
    }

```


## Filter For RadioBbutton
## HTML:

```
 <template if:true={dockedfrombottom}> <!-- Docked from Bottom radio Btn List / Template Start-->
            <div class="myclass-slds-docked-form-footer">
                <lightning-radio-group name="radioGroup" label="Sort by" options={radioSortOptions}
                    value={RadiosortValue} type="radio" onchange={onSelectRadioSortbyValue}></lightning-radio-group>
            </div>
        </template><!-- Docked from Bottom radio Btn List / Template End-->
```

## JS:
```
 onSelectRadioSortbyValue(event) {
        this.RadiosortValue = event.target.value;

        this.dockedfrombottom = false;
        this.ShowDetaisOfCreatedRecords = true;

        if (this.RadiosortValue === 'Newest to Oldest') {
        this.searchbarvalue = 'Partner Referral'
            this.OnSearchInLeadData();
            this.RadiosortValue = null;
            this.searchbarvalue = null;
        }
      
    }
```


## Shortcut of filter 

```
@track selectedFilter = null;

    handleCheckboxChange(event) 
    {
        const filterValues = {
            'Partner Referral': 'Partner Referral',
            'Web': 'Web',
            'Phone Inquiry': 'Phone Inquiry'
        };

        const label = event.target.label;
        this.selectedFilter = filterValues[label];
    }

onClickFilterButton() {
    this.showFilter = false;
    this.suspactPage = true;

    if (this.selectedFilter) {
        this[this.selectedFilter + 'CheckBox'] = false;
        this.searchKey = this.selectedFilter;
        this.searchLeads();
        this.searchKey = null;
        this.selectedFilter = null;
    }
}
```








