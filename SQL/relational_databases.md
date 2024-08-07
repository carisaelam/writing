# Relational Databases

***Relational Databases*** represent several tables that are related to one another. Kind of like several different tabs on Google Sheets that all represent the same project or problem and need to be able to interact with one another. Relationships between tables are defined using foreign keys that connect one table to the next. 


## Example 

**Users Table**

| UserID | Username   | Email              |
|--------|------------|--------------------|
| 1      | johndoe    | john@example.com   |
| 2      | janedoe    | jane@example.com   |
| 3      | alice      | alice@example.com  |

<p>&nbsp;</p>

**Orders Table**

| OrderID | UserID | OrderDate  | Amount |
|---------|--------|------------|--------|
| 101     | 1      | 2024-08-01 | 29.99  |
| 102     | 2      | 2024-08-02 | 49.99  |
| 103     | 1      | 2024-08-03 | 15.00  |

<p>&nbsp;</p>

**Products Table**

| ProductID | ProductName | Price |
|-----------|-------------|-------|
| 1001      | Widget       | 19.99 |
| 1002      | Gadget       | 24.99 |
| 1003      | Doodad       | 9.99  |

<p>&nbsp;</p>

