# Apex Testing 

## For fetch Data Method

Apex Method.apex
```
// To Fetch Seeds data
    @AuraEnabled
    public static List<Seeds__c> FetchAllSeeds() {
      List<Seeds__c> AllSeeds = [
      Select Id, Read_More__c, Name, Recommanded_Season__c,
      Information_del1__c, Image_Url__c FROM Seeds__c
      ];
     System.debug(AllSeeds);
    return AllSeeds;
   }
```


Apex Method.test
```
 static void testFetchAllSeeds() {
        Seeds__c seed1 = new Seeds__c(Name = 'Seed1', Recommanded_Season__c = '	Winter', Information_del1__c = 'Info1', Image_Url__c = 'URL1');
        Seeds__c seed2 = new Seeds__c(Name = 'Seed2', Recommanded_Season__c = 'Summer', Information_del1__c = 'Info2', Image_Url__c = 'URL2');
        insert new List<Seeds__c>{seed1, seed2};

        List<Seeds__c> resultSeeds = AgricultureEmpowerment.FetchAllSeeds();
        
        System.assertEquals(2, resultSeeds.size(), 'Expected 2 seeds');
        System.assertEquals('Seed1', resultSeeds[0].Name, 'Unexpected seed name');
        System.assertEquals('Winter', resultSeeds[0].Recommanded_Season__c, 'Unexpected recommended season');
        System.assertEquals('Seed2', resultSeeds[1].Name, 'Unexpected seed name');
        System.assertEquals('Summer', resultSeeds[1].Recommanded_Season__c, 'Unexpected recommended season');
    }
```



## For Insert Data Method

Apex Method.apex
```
@AuraEnabled
  public static String insertFeedback(String queryValue){
      List<Feedbacks__c> FeedbackList = new List<Feedbacks__c>();
      
      Feedbacks__c feedback = new Feedbacks__c();
      feedback.Feedback__c = queryValue;
      feedback.Submission_Date__c = System.Today();
      FeedbackList.add(feedback);
      insert FeedbackList;
      System.debug(feedback);
      return 'Query Inserted Succesfully!';
  }
```

Apex Method.test
```
  @isTest
    static void testInsertFeedback() {
        String queryValue = 'TestFeedback';
        String result = AgricultureEmpowerment.insertFeedback(queryValue);

        List<Feedbacks__c> resultFeedbacks = [SELECT Id, Feedback__c FROM Feedbacks__c];
        System.assertEquals(1, resultFeedbacks.size(), 'Expected 1 feedback entry');
        System.assertEquals(queryValue, resultFeedbacks[0].Feedback__c, 'Unexpected feedback value');
    }
```
