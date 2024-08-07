# Intro to SQL 

**SQL is like Google Sheets on steroids**


## WHERE
Use ```WHERE``` when you want to select certain rows. 

## WHEN 


I was moving and grooving until it was time to learn about ```INNER JOIN```. 


### How I currently understand ```INNER JOIN```

Consider this block 
```
SELECT first_element.attribute, second_element.attribute
FROM first_element
INNER JOIN second_element
ON first_element.id = second_element.id_that_corresponds
```
You start by selecting the two elements you are interested in joining together. This is your "end goal."  
We're going ```FROM``` the first element's table 
and ```INNER JOIN```ing it with the second element's table. 

But we have to tell SQL how the data in the two tables correspond. 
So we use ```ON``` to point out the two lines of data that represent the same thing. In our case, that is first_element.id and then second_element.id_that_corresponds to the first_element's table. 

* First table = "Left table"; in other words, the first one you list. 

* ```INNER JOIN``` will only show rows where data exists for both elements. ```LEFT JOIN``` will return all of the data from the first ("Left") table regardless of whether matching data exist in the other table. 

* With multiple ```INNER JOIN``` statements, it is like you are following the common thread to eventually connect your two dots. It's a lot like a linked list or some kind of tree. Some tables only point to data in other tables, but you can follow the data until you get what you need. Sometimes that requires going through two (or maybe more) ```INNER JOIN``` statements in order to create the connection you need. 


## Aliases 
* Aliases are basically just **nicknames** we give to elements to help our queries not be so long. 
* You can give a table an alias by writing ```AS alias_name``` right after the table name. 
* You can do the same thing for a column by writing ```AS alias_name``` right after the column name. 


## Like
* The ```LIKE``` command can be used to search text-based values. 
* ```_``` = one character 
* ```%``` = zero, one, or multiple characters 

> **Example**
> ```LIKE "TOTAL%"``` matches "TOTAL," "TOTAL1," "TOTAL ABC," etc. 
> ```LIKE "TOTAL_"``` matches "TOTAL 1," "TOTAL Z," "TOTAL A"


## Case 
* Use ```CASE``` when you want to return certain values on a conditional basis. 
* Very much like an ***if*** ***else*** statement 
```
SELECT * 
CASE WHEN (some condition) THEN (some value) ELSE (some value) END
rest of code...
```

## Substring (SUBSTR)
* Use this format: 
```SUBSTR(column_name, index, number_of_characters)```
* index starts at 1 (not zero)

## Coalesce
* You give it a list of columns, and it returns the value of the ***first*** column that isn't null. 