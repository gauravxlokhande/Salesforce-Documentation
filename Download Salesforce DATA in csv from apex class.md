```
// Define the wrapper class to hold account data
public class AccountCSVWrapper {
    public String AccountId { get; set; }
    public String AccountName { get; set; }
    public String AccountType { get; set; }
    public String Industry { get; set; }
    public String Phone { get; set; }

    // Constructor to initialize the wrapper with data from an Account record
    public AccountCSVWrapper(Account acc) {
        this.AccountId = acc.Id;
        this.AccountName = acc.Name;
        this.AccountType = acc.Type;
        this.Industry = acc.Industry;
        this.Phone = acc.Phone;
    }
}

// Class to generate CSV
public class CSVGenerator {
    // Method to generate CSV content from Account records
    public String generateCSV(List<Account> accounts) {
        List<AccountCSVWrapper> wrappers = new List<AccountCSVWrapper>();

        // Populate the wrappers list with Account data
        for (Account acc : accounts) {
            wrappers.add(new AccountCSVWrapper(acc));
        }

        // Now, generate the CSV content
        String csvContent = '';

        // Add the CSV header
        csvContent += 'AccountId,AccountName,AccountType,Industry,Phone\n';

        // Add the records data to the CSV
        for (AccountCSVWrapper wrapper : wrappers) {
            csvContent += wrapper.AccountId + ',';
            csvContent += '"' + wrapper.AccountName + '",';
            csvContent += '"' + wrapper.AccountType + '",';
            csvContent += '"' + wrapper.Industry + '",';
            csvContent += '"' + wrapper.Phone + '"\n';
        }

        return csvContent;
    }
}

// Anonymous Apex to handle bulk data and CSV creation
try {
    List<Account> accounts;
    Integer offset = 0;
    Integer batchSize = 2000; // Change this to the batch size you want
    String csvData = 'AccountId,AccountName,AccountType,Industry,Phone\n';
    
    // Create an instance of CSVGenerator to use the generateCSV method
    CSVGenerator csvGenerator = new CSVGenerator();
    
    // Query the accounts in batches to avoid governor limits
    while (true) {
        accounts = [SELECT Id, Name, Type, Industry, Phone FROM Account LIMIT :batchSize OFFSET :offset];
        
        if (accounts.isEmpty()) {
            break;
        }
        
        // Append records to CSV data
        csvData += csvGenerator.generateCSV(accounts);
        
        // Increment offset for next batch
        offset += batchSize;
    }

    // Create ContentVersion (file) with the CSV data
    ContentVersion contentVersion = new ContentVersion();
    contentVersion.Title = 'Accounts_Data';
    contentVersion.PathOnClient = 'accounts_data.csv';
    contentVersion.VersionData = Blob.valueOf(csvData);
    insert contentVersion;

    // Output the result to debug log
    System.debug('CSV file created and saved in ContentVersion with ID: ' + contentVersion.Id);
    System.debug('CSV file can be downloaded from: ' + '/sfc/servlet.shepherd/version/download/' + contentVersion.Id);

} catch (Exception e) {
    System.debug('Error: ' + e.getMessage());
}

```
