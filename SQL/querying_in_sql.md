# Querying in SQL

**SQL is like Google Sheets on steroids**

## SELECT

- Allow us to retrieve data from a database
- Often referred to simply as a "query"
- Tables are like objects
  - each row is an instance of that object
  - each column is a property

<p>&nbsp;</p>

**Table Name = neighbors**
|ID |Name |Age |State |
|-----|-------|------|------|
|1 |Jen |40 |NY |
|2 |Mark |42 |AL |
|3 |Tom |30 |GA |

A basic query would select a couple of columns with all of the rows.

`SELECT age, state FROM neighbors;`

Should return something like this:
**Table Name = neighbors**
|Age |State |
|------|------|
|40 |NY |
|42 |AL |
|30 |GA |

Use as asterisk (\*) to retrieve all of the columns of data at once.

<p>&nbsp;</p>

## WHERE

- Use `WHERE` when you want to select certain rows.
- The `WHERE` condition will be applied to each row of data to determine whether or not to include it in the results.

<p>&nbsp;</p>

**Table Name = neighbors**
|ID |Name |Age |State |
|-----|-------|------|------|
|1 |Jen |40 |NY |
|2 |Mark |42 |AL |
|3 |Tom |30 |GA |

`SELECT * FROM neighbors WHERE age < 41`

Should return:
**Table Name = neighbors**
|ID |Name |Age |State |
|-----|-------|------|------|
|1 |Jen |40 |NY |
|3 |Tom |30 |GA |

### Operators for using `WHERE` with text data

| Operator              | Condition                               |
| --------------------- | --------------------------------------- |
| = , !=, <>            | Case sensitive                          |
| LIKE/NOT LIKE         | Case insensitive                        |
| IN(...) / NOT IN(...) | String does or does not exist in a list |

<p>&nbsp;</p>


### Like

- The `LIKE` command can be used to search text-based values.
- `_` = one character
- `%` = zero, one, or multiple characters

> **Example** > `LIKE "TOTAL%"` matches "TOTAL," "TOTAL1," "TOTAL ABC," etc.
> `LIKE "TOTAL_"` matches "TOTAL 1," "TOTAL Z," "TOTAL A"

<p>&nbsp;</p>



## Filtering and Sorting Results 
- Use the `DISTINCT` keyword to remove rows that have the same column value. In other words, it removes duplicates from the results. The keyword comes right after `SELECT`
- Use `ORDER BY` to sort by a specific column 
- Use `LIMIT` to only return 'x' number of results 
- Use `OFFSET` to tell SQL where to begin counting the rows 
- `LIMIT` and `OFFSET` are typically written at the end of a query

<p>&nbsp;</p>

## 🔥 JOIN ☠️
Most real-world data is stored across multiple related tables. Tables sharing information about the same object have to use ***primary keys*** to keep up with unique entities. 

The most commonly used primary key is an auto-incrementing integer (starts at one, increases by one for each row added.)

<p>&nbsp;</p>

### Types of `JOIN`
1. `INNER JOIN`
2. `LEFT JOIN`
3. `RIGHT JOIN`
4. `FULL JOIN`

LEFT, RIGHT, and FULL JOIN are used when data is asymmetrical... when it doesn't exactly line up in every table, or when some information is missing. 

### How I currently understand `INNER JOIN`

Consider this block

```
SELECT first_table.column, second_table.column
FROM first_table
INNER JOIN second_table
ON first_table.id = second_table.id_that_corresponds
```

You start by selecting the two elements you are interested in joining together. This is your "end goal."  
We're going `FROM` the first element's table
and `INNER JOIN`ing it with the second element's table.

But we have to tell SQL how the data in the two tables correspond.
So we use `ON` to point out the two lines of data that represent the same thing. In our case, that is first_element.id and then second_element.id_that_corresponds to the first_element's table.

- First table = "Left table"; in other words, the first one you list.

- `INNER JOIN` will only show rows where data exists for both elements. `LEFT JOIN` will return all of the data from the first ("Left") table regardless of whether matching data exist in the other table.

- With multiple `INNER JOIN` statements, it is like you are following the common thread to eventually connect your two dots. It's a lot like a linked list or some kind of tree. Some tables only point to data in other tables, but you can follow the data until you get what you need. Sometimes that requires going through two (or maybe more) `INNER JOIN` statements in order to create the connection you need.

<p>&nbsp;</p>

## Aliases

- Aliases are basically just **nicknames** we give to elements to help our queries not be so long.
- You can give a table an alias by writing `AS alias_name` right after the table name.
- You can do the same thing for a column by writing `AS alias_name` right after the column name.

<p>&nbsp;</p>

## Aggregate Functions
**Common Aggregate Functions**
1. `COUNT`
2.  `MIN` / `MAX`
3. `AVG`
4. `SUM`

`GROUP BY` allows you to group rows together that have the same value in one of the columns. 

## Case

- Use `CASE` when you want to return certain values on a conditional basis.
- Very much like an **_if_** **_else_** statement

```
SELECT *
CASE WHEN (some condition) THEN (some value) ELSE (some value) END
rest of code...
```

<p>&nbsp;</p>

## Substring (SUBSTR)

- Use this format:
  `SUBSTR(column_name, index, number_of_characters)`
- index starts at 1 (not zero)

<p>&nbsp;</p>

## Coalesce

- You give it a list of columns, and it returns the value of the **_first_** column that isn't null.

<p>&nbsp;</p>

## Order of Execution 
1. `FROM` and `JOIN`
2. `WHERE`
3. `GROUP BY`
4. `HAVING`
5. `SELECT`
6. `DISTINCT`
7. `ORDER BY`
8. `LIMIT / OFFSET`

<p>&nbsp;</p>

## Acknowledgements

[SQLBolt](https://sqlbolt.com/lesson/select_queries_introduction)
