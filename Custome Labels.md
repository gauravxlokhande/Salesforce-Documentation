# Custome Lables in Salesforce

## custome lables is used to change the website content into different languages.

## method to get the custome label in apex from org
```
String storecustomelabel = System.label.get('', 'Api_name', 'en') // en is the english language code search on gooogle
System.debug(storecustomelabel);
```

```
Step 1:custom labels // open in org in quick find
Step 2: Language Setting // to add all languages in it
Step 2: Translation Language Setting // to add the different languages in it
Step 3: Translate // by using this we can change object picklist language
```
