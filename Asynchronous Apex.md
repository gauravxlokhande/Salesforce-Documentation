# Batchable Apex

```
global class TestBatchApex implements Database.Batchable<sObject>, Database.Stateful {
    
    global Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator([SELECT Id, Phone, Name FROM Account]); // here we query all the records from the SObject.
    }

    global void execute(Database.BatchableContext bc, List<Account> accListt) {
        List<Account> accountsToUpdate = new List<Account>();

        for (Account acc : accListt) {
            if (String.isBlank(acc.Phone)) {                                  //here we peform all the operations on the above queryed object list.
                acc.Phone = '9511767637';
                accountsToUpdate.add(acc);
            }
        }

        // Bulk update outside of the loop
        if (!accountsToUpdate.isEmpty()) {
            update accountsToUpdate;
        }
    }

    global void finish(Database.BatchableContext bc) {
        System.debug('Batch job id = ' + bc.getJobId());               // here we peformed the final action like : Send email, notification , or debug etc..
    }
}

```

## To Execute This Class:

```
Id jobid = Database.executeBatch(new TestBatchApex(), 200);     // it is a reference of new TestBatchApex() and 200 is a size of batch that gonna bu execute at a time
System.debug('jobid'+jobid);                                    // it returns a jobid ike 200record execute is a batch so it retun its id.
```
