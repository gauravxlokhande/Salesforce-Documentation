# Add try catch block in apex also store error in a record. for handling errors in production.

## Create a custome object named Error_Log__c
![image](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/84ccc0ea-8349-442f-a711-d288db66ed07)

## add this fields in it.
![image](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/c0a20ef0-4c8b-4d45-bb2a-3152ff46e562)


HandleError.cls
```
public class HandleError {
    public static void ErrorLog( String ClassName, String MethodName, String RefId, exception ex){
        Error_Log__c Elog = new Error_Log__c();
        Elog.Class_Name__c =ClassName;
        Elog.Method_Name__c=MethodName;
        Elog.Stack__c=ex.getStackTraceString();
        Elog.Error_Message__c =ex.getMessage();
        if(!string.isBlank(RefId)){
            Elog.Reference_Id__c =RefId;
        }
        insert Elog;
    }
}
```

```
 HandleError.ErrorLog('ClassName','MethodName','RefId/ null', ex);
```

## Use Above Error clss for creating the record of errors in any apex class Like:

theclassuwnattohandleerror.cls
```
public class TestingTryCatch {
    public static void trycatchtest(){
        try{
            Account acc =[Select id,Name From Account Where Name='gaurav'];
            String storename =String.valueOf(acc.Name);
        }catch(exception ex){
            HandleError.ErrorLog('TestingTryCatch','trycatchtest',null, ex);  // use above class to create record of any failing method error.
        }
    }

}
```


## Like Below i got the record created for error of above apex class

![image](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/33e455b6-2e75-4c0f-8070-06bf7016987e)

