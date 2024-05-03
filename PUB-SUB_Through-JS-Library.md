# Pub SUb Trough js Library.

# Step 1:

## Create one LWC Component file in vs code without html and test file in it. having name "pubsub".
![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/21f511da-f6b3-4e2c-adba-2ca25590cd00)

## SENDER
## then create the "Publisher component" from which ur sending the data:
- we ned to import "Currentpagereference" & the pubsub component.
  
![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/8e8c3208-8b04-4c34-99d8-8d292aeb34e3)

- after that the data we need to send add this in fireEvent
- in fireevent we pass reference of currentpage, namefordata, and data.

![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/37bf122d-56de-4cc3-ae8e-daffe7b6cbfa)

## Reciever
## create the "Sucriber component" that getting the data
 -same for it we need to import currentpagerefrence. then import registerlistener and unregisterlistner.
 
 ![image](https://github.com/gauravxlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/b70e5034-867b-4c0b-8f95-d1da63821ecf)

- in registerlistner we pass nameofevent and the variable in which we need data and the refrence of current page.

# NOTE : same as the data we are getting in reciever we can get data in any component just we need to repeat the steps that we used in reciever. 
Eg: we get accountId in any component according above note.
