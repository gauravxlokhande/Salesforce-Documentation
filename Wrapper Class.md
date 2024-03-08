
# Wrapper Class In Salesforce

## Basic Syntax of wrapper class.
```
public class AgricultureWrapper {
    public static List<records> gavecududu(){
        List<records> reclist = new List<records>();
        records rec =new records();
        rec.state='pune';
        reclist.add(rec);
        System.debug(reclist);
        return reclist;
    }
    public class records {
        public String state;    // Bihar
        public String district;    // Rohtas
        public String market;    // Sasaram
        public String commodity;    // Onion
        public String variety;    // Medium
        public String grade;    // NA
        public String arrival_date;    // 17/12/2023
        public String min_price;    // 3500
        public String max_price;    // 4500
        public String modal_price;    // 4000
    }
}
```




## overall i learn by exploring this wrappper class concept is the wrapper class is a class that have power to contain the different data types of data and resturn differnt data types of data by combining in a single object.

Ex:  the best example of it is the one class that returning in result is:  | Account Name | Contact Name | Total no of related contact|

```
public class WrapperClass {
    public string HospitalName;
    public string HospitalLocation;
    
    List<Doctor> docList = new List<Doctor>();   // data type claaa list
    
    public void adddoctor(String Name, Integer Age, String Speciality ){    // normal data get method
        Doctor doc =new Doctor(Name,Age,Speciality);             // passing values to constructor
        docList.add(doc);    // storing data in list
    }
    
    public void getdoctor(){         // to get data this method used
        for(doctor d: docList){        // iterate over data
            System.debug(d.Name);
             System.debug(d.Age);
             System.debug(d.Speciality);
            
        }
    }

   
     Private class Doctor{      // class 
        private String Name;
        private Integer Age;
        private String Speciality;
        
        Doctor( String Name, Integer Age, String Speciality ){   // constructorr
            this.Name =Name;
            this.Age =Age;
            this.Speciality =Speciality; 
        }
    }
}

```

## Example 1
```
public with sharing class AccountContactWrapper {
    @AuraEnabled(cacheable=true)
    public static List<WrapperClass> getWrapAccountList() {
        return fetchAccountContactData();
    }

    private static List<WrapperClass> fetchAccountContactData() {
        List<WrapperClass> wrapAccountList = new List<WrapperClass>();
        for (Account acc : [SELECT Id, Name, (SELECT Id, Name, Email FROM Contacts) FROM Account LIMIT 100]) {
            wrapAccountList.add(new WrapperClass(acc, acc.Contacts, acc.Contacts.size()));
        }
        System.debug(wrapAccountList);
        return wrapAccountList;
    }

    // This wrapper class 
    public class WrapperClass {
        @AuraEnabled
        public Account acc { get; set; }
        @AuraEnabled
        public List<Contact> conList { get; set; }
        @AuraEnabled
        public Integer contactSize { get; set; }
        @AuraEnabled
        public Boolean isCheck { get; set; }

        public WrapperClass(Account a, List<Contact> cont, Integer countContact) {
            this.acc = a;
            this.conList = cont;
            this.contactSize = countContact;
            this.isCheck = false;
        }
    }
}


```

## Example 2 
 ## Solved by me
```
public without sharing class AccountContactWrapper {
  
    
     Public  List<FetchAllData> fetchAccountContactData() {
   List<FetchAllData> allDataList =new List<FetchAllData>();
    
    List<Account> acclist =[Select Id, Name,(Select Id,Name, Email From Contacts) From Account Limit 10];
    
    for(Account add: acclist){
        allDataList.add(new FetchAllData(add, add.Contacts, add.Contacts.size()));
    }
         System.debug(allDataList);
         return allDataList;
     } 
    
    
    public class FetchAllData{
        
        Public Account acc;
        Public List<contact> con;
        Public Integer ContactSize;
        Public Boolean IsCheck;
         
        FetchAllData(Account A, List<Contact> conl , Integer ConSize){
             this.acc =A;
             this.con=conl;
             this.ContactSize =ConSize;
        }         
    }
    
    
}

```



# To gave data to another org/ we can acces in postman

<img width="518" alt="Screenshot 2024-01-02 111219" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/f28565b5-5507-4a59-9ae2-5902a2c21f45">



# Wrapper Class Selected Accounts multiple
```
https://youtu.be/CWoAGoLjr7c?si=pQvNB5ZwemP7-JiW
```
<img width="510" alt="Screenshot 2024-01-02 125914" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/26cf1200-15e3-4f46-8c3d-5050ab4c4255">


