## Show the related field data in lwc:

if any record having any lookup or MD field and you want to show their data and access ther data then u need too use objectname__r.fieldname

```
  <div class="allInformation" key={event.Id}>
                        <div>
                            <h1><b>SOCIETY : </b>{event.Society__r.Name}</h1>
                            <h1><b>ORGANIZER : </b>{event.Organizer__r.Name}</h1>
                            <h1><b>ELIGIBILITY : </b>{event.Eligibility__c}</h1>
                        </div>
                    </div>
```

```
public with sharing  class SocietyManagementSystem {

    @AuraEnabled(Cacheable=true)
  public static List<Event__c> SearchEvents(String searchinit) {
    String keystring = '%' + searchinit + '%';
    return [SELECT Id, Name, Date_and_Time__c, Location__c,Organizer__r.Name,Society__r.Name, Event_Image__c, Eligibility__c FROM Event__c WHERE Date_and_Time__c >= TODAY AND Name LIKE :keystring];
   }

    
}
```
