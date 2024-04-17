# Aggregate Functions FOr SUM COUNT 

## Update total amount of account related opportunity on related account.
```
public class TotalOppAmounntAccHandler {

    public static void TotalOppAmounntAccHandlerMethod(List<Opportunity> oppList){
        
        Set<Id> SetAccountId = new Set<Id>();
        
        for(Opportunity opp : oppList){
            SetAccountId.add(opp.AccountId);
        }
        
        Map<Id, Decimal> accountIdToTotalAmount = new Map<Id, Decimal>();
        
        for(AggregateResult res : [SELECT AccountId, SUM(Amount) TotalAmount FROM Opportunity WHERE AccountId IN :SetAccountId GROUP BY AccountId]){
            accountIdToTotalAmount.put((Id)res.get('AccountId'), (Decimal)res.get('TotalAmount'));
        }
        
        for(Opportunity opp : oppList){
            Account acc = new Account(Id = opp.AccountId);
            acc.Total_Amount_Of_All_Opportunity__c = String.valueOf(accountIdToTotalAmount.get(opp.AccountId));
            update acc;
        }
    }
}

```
