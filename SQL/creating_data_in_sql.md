# Creating Data in SQL

**SCHEMA**: describes the structure of the table (i.e., what data type each column should be)

## Insert

`INSERT INTO` => used to insert a new row into a table
`INSERT INTO table_name VALUES (value1, value2, value3)`

<p>&nbsp;</p>

## Update

`UPDATE` => used to update existing data

```
UPDATE table_name
SET column1 = value1,
    column2 = value2,
WHERE condition;
```

**Pro-tip:** Test the update out via a SELECT query first before actually implementing it.

<p>&nbsp;</p>

## Delete

`DELETE` => used to delete a specific row using a `WHERE` clause

```
DELETE FROM table_name
WHERE condition;
```

**Pro-tip:** Like with `UPDATE`, always test it out via a SELECT query first before actually implementing `DELETE`.

<p>&nbsp;</p>

## Creating Tables

`CREATE TABLE` => creates a new table from scratch
The table schema lays out the name of the table, the type of data for each column, any constraints the columns will use, and any default values

```
CREATE TABLE IF NOT EXISTS table_name (
  id INTEGER PRIMARY KEY,
  name TEXT,
  age INTEGER,
  registered BOOLEAN
)
```

**Pro-tip:** Use `IF NOT EXISTS` after `CREATE TABLE` to prevent errors.

**COMMON CONSTRAINTS**

- PRIMARY KEY
- AUTOINCREMENT (not supported in all databases)
- UNIQUE

<p>&nbsp;</p>

## Adding and Removing Columns

`ALTER TABLE` => used to change the number of columns or constraints

**Adding a column**

```
ALTER TABLE table_name
ADD column INTEGER PRIMARY KEY
  DEFAULT optional_default_value;
```

**Deleting a column**
*not supported in SQLite

```
ALTER TABLE table_name
DROP column_name;
```

**Renaming a column**

```
ALTER TABLE table_name
RENAME TO updated_table_name;
```

**Deleting an entire table**

```
DROP TABLE IF EXISTS table_name;
```



<p>&nbsp;</p>
