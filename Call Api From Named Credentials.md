# Call Api From Named Credentials

```
public class CallAnimalAPI {  
    
    Public static void CallAnimalAPIMethod(){
        Http http = new Http();
        HttpRequest req = new HttpRequest();
        req.setEndpoint('Callout:CallAnimalApi/v1/animals?name=Cheetah');
        req.setMethod('GET');
        HttpResponse res = http.send(req);
        if(res.getStatusCode()==200){
                   System.debug(res.getBody()); 
        }else{
            System.debug('Api Data Not Getting');
        }

    }    
}
```

![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/ab906315-ec80-4e5d-a38c-1a3b52f28109)
![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/e0f73747-74be-4470-93b7-4fb65bef9188)

