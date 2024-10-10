# Soql Queries

### Scenario:
Imagine you want to retrieve a list of accounts that have opportunities with a total value greater than $10,000, where the opportunities are in an "Open" stage and created in the last 90 days. For each account, you want to include the account name, the number of opportunities, and the total value of those opportunities.

### SOQL Query:
```sql
SELECT 
    Id, 
    Name, 
    (SELECT                        // query child records inside the parent records baseed on coditions
        COUNT(Id), 
        SUM(Amount) 
     FROM 
        Opportunities 
     WHERE 
        StageName = 'Open' 
        AND CreatedDate = LAST_N_DAYS:90 
     GROUP BY 
        AccountId 
     HAVING 
        SUM(Amount) > 10000)
FROM 
    Account 
WHERE 
    Id IN (SELECT                  // query another object records and put conditions on it and compare it with the queried record parentid by fetching related record accountid 
        AccountId 
        FROM 
        Opportunity 
        WHERE 
        StageName = 'Open' 
        AND CreatedDate = LAST_N_DAYS:90 
        GROUP BY                            // we can ise groupby  whenever we use aggregate query
        AccountId 
        HAVING                                      // by using having only we can peform action/conditions on aggrect functions
        SUM(Amount) > 10000)
```

### Explanation:
1. **Outer Query**:
   - Selects `Id` and `Name` from the `Account` object.
   - Filters accounts using a subquery that looks for opportunities.

2. **Subquery for Opportunities**:
   - Counts the number of opportunities and sums their amounts.
   - Filters to include only opportunities that are "Open" and created in the last 90 days.
   - Groups by `AccountId` and uses `HAVING` to ensure the total amount is greater than $10,000.

3. **Filtering Accounts**:
   - The outer `WHERE` clause checks if the account has any opportunities meeting the specified criteria.

\
