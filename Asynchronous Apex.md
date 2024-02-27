# Batchable Apex
<p> In Batch Apex we decide that we want to update records, delete records or insert records in bulck manner, Batch Apex jobs are limited to five tasks running simultaneously for fast result and executeBatch can have a maximum value of 2,000.  </p>

<p>A maximum of 50 million records can be returned in the QueryLocator object. If more than 50 million records are returned, the batch job is immediately terminated and marked as Failed.</p>

<p>We can also shedule batch class from itself by: Database.Batchable<sObject>,Schedule </p>


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

// ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
  global void execute(SchedulableContext ctx) {
        Id Jobid =  Database.executeBatch(new TestBatchApex(), 200); // for sheduling batch class from itself
        System.debug(Jobid);
    }
// ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
}

```

## To Execute This Class:

```
Id jobid = Database.executeBatch(new TestBatchApex(), 200);     // it is a reference of new TestBatchApex() and 200 is a size of batch that gonna bu execute at a time
System.debug('jobid'+jobid);                                    // it returns a jobid ike 200record execute is a batch so it retun its id.
```


# Scheduled Class
<p> Sheduled class is used for scheduled the batchable classes on the perticular time or a perticular day</p>

<p>there are the two ways of Sheduled a class: 1. From UI , 2. By using CRON Expression</p>

## Sheduled Class From UI
Apex Classes--> Scheduled Class--> Schedule

```
global with sharing class ScheduledtestClass implements Schedulable {
    
    global void execute(SchedulableContext ctx) {
        Id Jobid =  Database.executeBatch(new TestBatchApex(), 200);
        System.debug(Jobid);
    }
    
}
```

## To execute this class

```
String CRON_EXP = '0 0 0 3 9 ? 2042';
System.schedule('ScheduleClassNameStr - Monday 5AM', CRON_EXP, new ScheduledtestClass());
```


# Queueable Class
<p> we can also do job chaining like we can call the class2 from class1.</p>

## To Execute job
```
 system.enqueuejob( new SampleQueueable1());
```
Class 1:
```
global with sharing class SampleQueueable1 implements Queueable { 
    global void execute(QueueableContext context) {
        Account acc = new Account();
         acc.Name='Gaurav';
         Insert acc;
    }
ID jobid = system.enqueuejob( new SampleQueueable2());
System.debug(jobid);
}
```

Class 2:
```
global with sharing class SampleQueueable2 implements Queueable { 
    global void execute(QueueableContext context) {
        Contact con = new Contact();
         con.Name='Gaurav';
         Insert con;
    }
}
```
