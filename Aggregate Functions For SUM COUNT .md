# Aggregate Functions FOr SUM COUNT 
```
trigger UpdateAccount on Account (after update) {
    
    Set<Id> accId = new Set<Id>();
    
    for(Account acc:Trigger.new){
        accId.add(acc.Id);
    }
    
    List<AggregateResult> AllOpp =[Select AccountId , sum(Amount)Totalamount From Opportunity Where AccountId IN: accId group by AccountId];
    
    map<Id, String> updateaccount =new map<Id, String>();
    
    for(AggregateResult agri: AllOpp){
        Id accIds =(Id) agri.get('AccountId');
        String totalamt =(String) agri.get('Totalamount');
        updateaccount.put(accIds, totalamt);
    }
    
    List<Account> accounttoupdate =new List<Account>();

    for(Account ac:Trigger.new){
        if(updateaccount.containskey(ac.Id)){
            ac.Description =updateaccount.get(ac.id);
            accounttoupdate.add(ac);
        }
    }
    if(!accounttoupdate.isEmpty()){
        update accounttoupdate;
    }
}
```
