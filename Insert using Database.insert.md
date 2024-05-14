# Database.Insert( List, false)

## database.insert(list,false)  it works when we need to insert multple records and some records have error then if we user insert then all records get back from insertion insted of this if we use database.insert() and insert the records then only the records having problems or error get back insted all records get inserted successfull.

Example:

```
List<Account> accounts = new List<Account>{
    new Account(Name = 'Acme Corporation', Phone = '123-456-7890',Account_Balance__c=3223),
    new Account(Name = 'Global Enterprises', Phone = '987-654-3210',Account_Balance__c=322),
    new Account(Name = '',Account_Balance__c=3223) // This will fail because Name is required
};

List<Database.SaveResult> results = Database.insert(accounts, false);

for (Database.SaveResult sr : results) {
    if (sr.isSuccess()) {
        System.debug('Account inserted successfully. ID: ' + sr.getId());
    } else {
        System.debug('Error inserting account: ' + sr.getErrors()[0].getMessage());
    }
}

```
