
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
