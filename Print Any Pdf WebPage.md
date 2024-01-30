# To Print the whole WebPage

```
 handlePrint() {
        // Calling the window.print() method to trigger the print dialog
        window.print();
    }
```

## Know the concept of Files Object, Files object api name is contentdocument and its relation with two object one is contentdocumentlink and ContentVersion.

1. ContentDocument: when we upload a file it upload as content document.
2. contentdocumentlink: and ContentDocumentid is related to ContentDocumentLink
3. ContentVersion in this we check version like pdf, file or what?

```
public with sharing class PDFViewerController {
    @AuraEnabled(cacheable=true)
    public static Map<ID, String> getRelatedFilesByRecordId(String recordId) {
        // Get record file IDs        
        List<ContentDocumentLink> files = [SELECT ContentDocumentId FROM ContentDocumentLink WHERE LinkedEntityId = :recordId];
        List<ID> fileIDs = new List<ID>();
        for (ContentDocumentLink docLink : files) {
            fileIDs.add(docLink.ContentDocumentId);
        }

        // Filter PDF files 
        List<ContentVersion> docs = [SELECT ContentDocumentId, FileExtension, Title 
            FROM ContentVersion WHERE ContentDocumentId IN : fileIDs AND FileExtension='pdf'];
        Map<ID, String> mapIdTitle = new Map<ID, String>();
        for (ContentVersion docLink : docs) {
            mapIdTitle.put(docLink.ContentDocumentId, docLink.Title);
        }

        return mapIdTitle;
    }
}
```
