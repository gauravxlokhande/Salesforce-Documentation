# Custome Lables in Salesforce

## custome lables is used to change the website content into different languages.

## method to get the custome label in apex from org
```
String storecustomelabel = System.label.get('', 'Api_name', 'en') // en is the english language code search on gooogle
System.debug(storecustomelabel);
```

```
Step 1: storecustomelabel // open in org in quick find
Step 2: Translation Language Setting // to add the different languages in it
```
