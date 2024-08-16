# Active Record Queries Cheat Sheet

Active Record allows you to execute SQL commands using Ruby. This guide cuts through the fluff to provide **_a simple reference for some common Active Record queries_**. For each query, you’ll find the SQL equivalent and a brief description of what it returns, making it easy to see how the methods map to SQL commands.

&nbsp; 

**`find`**

- **SQL Equivalent:** `SELECT * FROM model WHERE (model.id = :id)`
- **Returns:** the record with the specific ID.

&nbsp; 

**`take`**

- **SQL Equivalent:** `SELECT * FROM model LIMIT 1`
- **Returns:** the record without any ordering
 
&nbsp; 

**`first`**

- **SQL Equivalent:** `SELECT * FROM model ORDER BY model.id ASC LIMIT 1`
- **Returns:** the record with the first primary key that exists

&nbsp; 

**`last`**

- **SQL Equivalent:** `SELECT * FROM model ORDER BY model.id DESC LIMIT 1`
- **Returns:** the record with the last primary key that exists

&nbsp; 

**`find_by`**

- **SQL Equivalent:** `SELECT * FROM model WHERE (model.parameter = 'foo') LIMIT 1`
- **Returns:** the first record matching the condition

&nbsp; 


_This is not meant to be an exhaustive guide._ 
For more information, see the [Rails Guides: Active Record Query Interface](https://guides.rubyonrails.org/active_record_querying.html#what-is-the-active-record-query-interface-questionmark). 
***

&nbsp; 
👋**Connect with me on [Github](https://github.com/carisaelam) or [LinkedIn](https://www.linkedin.com/in/carisa-elam-097368239). 
I'd love to hear your thoughts!**

