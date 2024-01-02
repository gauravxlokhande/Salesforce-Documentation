
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


<img width="518" alt="Screenshot 2024-01-02 111219" src="https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/41a8f01b-5347-46cb-9b30-8790942dc4f3">


