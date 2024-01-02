
# Wrapper Class In Salesforce


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

# To gave data to another org/ we can acces in postman

<img width="518" alt="Screenshot 2024-01-02 111219" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/41a8f01b-5347-46cb-9b30-8790942dc4f3">


# Wrapper Class Selected Accounts multiple
```
https://youtu.be/CWoAGoLjr7c?si=pQvNB5ZwemP7-JiW
```
<img width="510" alt="Screenshot 2024-01-02 125914" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/26cf1200-15e3-4f46-8c3d-5050ab4c4255">


