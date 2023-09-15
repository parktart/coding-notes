# SQL





## Intro

SQL has ANSI and ISO standards - so each Relational Database Management System (RDMS) must implement *at least* the standard functionality of SQL

And each RDMS will usually have *additional* functionality added on top of **standards-based SQL**

The notes in this file cover **standards-based SQL** only



## Normalization

The below table is an example of bad database design..

**Contact** table

| First Name | Last Name | Email1          | Email2            |
| ---------- | --------- | --------------- | ----------------- |
| John       | Flanders  | jon@gmail.com   | jonFlan@yahoo.com |
| Frizt      | Onion     | fritz@gmail.com | null              |

This design does not easily facilitate multiple email addresses per person



To facilitate multiple email addresses per person we implement Database Normalization

**Person** table

| Key  | First Name | Last Name |
| ---- | ---------- | --------- |
| 1    | Jon        | Flanders  |
| 2    | Fritz      | Onion     |

**Email** table

| Key  | Person Key | Email             |
| ---- | ---------- | ----------------- |
| 1    | 2          | fritz@gmail.com   |
| 2    | 1          | jon@gmail.com     |
| 3    | 1          | jonFlan@yahoo.com |



Database design will determine what queries will be possible later on



## Basic SQL Syntax

CRUD

C - Create - INSERT

R - Read - SELECT

U - Update - UPDATE

D - Delete - DELETE



`SELECT` retrieve one or more columns from one or more tables

```sql
SELECT <column> FROM <table> ;
```

```sql
SELECT first_name FROM person ;
```

`SELECT` and `FROM` here are SQL **keywords** and we use uppercase to denote so (though lowercase would be valid)

`first_name` and `person` here are **identifiers** 

`SELECT first_name` here is the **select clause** (select column)

`FROM person` here is the **from clause** (from table)





`INSERT`

Can only insert into one table at a time

```sql
INSERT INTO <table> (<column>, <column>) VALUES ('value', 'value') ;
```

```sql
INSERT INTO person (first_name, last_name) VALUES ('Guy', 'Richi') ;
```

notice how we didn't specify the `Key` as it is auto generated





`UPDATE` modify one or more rows in a table

```sql
UPDATE <table> SET <column> = 'value' WHERE <column> = 'value' ;
```

```sql
UPDATE person SET last_name = 'Smith' WHERE id = 1 ;
```





`DELETE` remove one or more rows from a single table

```sql
DELETE FROM <table> WHERE <column> = 'value' ;
```

```sql
DELETE FROM person WHERE id = 2 ;
```



## SQL Best Practices

Here are some database management conventions, these are not necessarily universal, and you should always follow the conventions of your team..

- SQL Keywords in upper-case

- Table names singular (not plural)

  - A table name should describe what each row contains, for example

    each row in a `Person` table is a person

- Column names should not be repeated inside a database (prefix all column names with the table name)



## SELECT

a `SELECT` statement is a *question* you are asking the database



the most basic `SELECT` statement doesn't even query a database..

```sql
SELECT 'Hi', 'Bye' ;
```

This statement returns a row with two columns

| Hi   | Bye  |
| ---- | ---- |

This seems like a weird SQL statement, but it can actually be quite useful for interjecting items that aren't actually contained in a database into your query

Here `'Hi', 'Bye'` is called the **select list**



We normally list columns we want to select in the **select list**

```sql
SELECT first_name, last_name FROM person ;
```

We can optionally **qualify** each column name with it's table name..

```sql
SELECT person.first_name, person.last_name FROM person ;
```



### Aliasing

To make this statment shorter..

```sql
SELECT person.first_name, person.last_name FROM person ;
```

we can **alias** the table name

```sql
SELECT p.first_name, p.last_name FROM person p ;
```

qualifying each column and aliasing table names is a **best practice**!



### Constraining

Above we selected all rows from the Person table, but we usually want to select only certain rows

There are two main ways to do this, with a..

1. DISTINCT Qualifier
2. WHERE Clause



#### DISTINCT Qualifier

`DISTINCT` (vs `NOT DISTINCT`)

 ```sql
 SELECT DISTINCT p.first_name FROM person p ;
 ```

will only return one row for each unique `first_name`

note..

```sql
SELECT DISTINCT p.first_name, p.last_name FROM person p ;
```

will only return one row for each unique `first_name` `last_name` *combination*



## WHERE

Filters our queries

```sql
SELECT p.first_name, p.last_name FROM person p
WHERE p.first_name = 'Jon' ;
```



### Operators

`=` Equals

`<>` Not equal to

`>` Greater than

`<` Less than

`>=` Greater than or equal to

`<=` Less than or equal to



#### AND

```sql
WHERE p.first_name = 'Jon' AND p.last_name = 'Flanders' ;
```

#### OR

```sql
WHERE p.first_name = 'Jon' OR p.last_name = 'Flanders' ;
```

#### BETWEEN

```sql
WHERE p.age BETWEEN 12 AND 30 ;
```

BETWEEN is **inclusive** (>= , <=)

#### LIKE

Is a sort of 'fuzzy' version of `=`

we can use wildcards

```sql
WHERE p.first_name LIKE 'J%' ;
```

`%` anything

#### IN

Is a sort of multi-value version of `=`

List of potential values, true if any of the values match

using `OR`..

```sql
WHERE p.first_name = 'Jon' OR p.first_name = 'Bob' ; 
```

using `IN`..

```sql
WHERE p.first_name IN ('Jon' , 'Bob') ;
```

#### IS

Special version of `=` used for NULL

```sql
WHERE p.last_name IS NULL ;
```

```sql
WHERE p.last_name IS NOT NULL ;
```

always used with NULL as `IS NULL` or `IS NOT NULL`

can only be used on nullable columns



## Shaping Results

#### ORDER By

Sorts a result set

Can specify one or more columns to order by (will order by the first one, then order by again, and again, etc)

ASC (default) or DESC - ascending or descending

```sql
SELECT p.first_name, p.last_name FROM person p
ORDER BY p.last_name ;
```



#### Set Functions

Compute new values from column values

Often used with DISTINCT



`COUNT`

Returns number of rows for a specified column (number of rows that are not NULL)

```sql
SELECT COUNT(*) FROM person p ;
-- total number of rows in the table

SELECT COUNT(p.email) FROM person p ;
-- number of rows that contain an email

SELECT COUNT(p.first_name) FROM person p
WHERE p.first_name = 'Jon' ;
-- number of rows with a first name of Jon
```



`MAX`

Maxiumum value in a column (excludes NULL values)

```sql
SELECT MAX(p.age) FROM person p ;
```



`MIN`

Minimum value in a column (excludes NULL values) 

```sql
SELECT MIN(p.age) FROM person p ;
```



`AVG`

Average value of column (excludes NULL values - only for numeric columns)

```sql
SELECT AVG(p.age) FROM person p ;
```



`SUM`

Sum of all values in a column (excludes NULL values - only for numeric columns)

```sql
SELECT SUM(p.money) FROM person p ;
```



Example with `DISTINCT`

```sql
SELECT COUNT(DISTICT p.first_name) FROM person p ;
-- count of unique first names
```



#### GROUP BY

Allows multiple columns in a set function

Breaks result set into subsets

Runs set function against each subset

Returns 1 row per subset

The subset is dictated by the column in GROUP BY (this column must appear in the SELECT list)

```sql
SELECT COUNT(p.first_name), p.first_name
FROM person p 
GROUP BY p.first_name ;
-- what are the unique first names and what is the count for each
```



#### HAVING

HAVING restricts the result sets formed by GROUP BY

```sql
SELECT COUNT(p.first_name), p.first_name
FROM person p
GROUP BY p.first_name
HAVING COUNT(DISTINCT p.first_name) > 1 ;
-- what are the unique first names that appear more than once and what is the count for each
```





## Combining Data

### JOINS

Merges multiple tables into one result set

Typically used with a WHERE Clause



`CROSS JOIN`

Simplest join - returns all rows from both tables - inefficient

CROSS keyword is not actually needed because CROSS is implied by the syntax, for example..

```sql
SELECT p.first_name, e.email_address
FROM person p, email_address e ;
```

this is bad practice bc it is inefficient and the data will be all screwed up - you need a WHERE Clause!

Tables:

| Person GUID | First Name | Last Name |
| ----------- | ---------- | --------- |
| 1           | Jon        | Smith     |
| 2           | Paul       | Ruby      |
| 3           | Mark       | Presto    |

| Email GUID | Person GUID | Email Address        |
| ---------- | ----------- | -------------------- |
| 1          | 3           | markpresto@gmail.com |
| 2          | 1           | jonsmith@gmail.com   |
| 3          | NULL        | someone@gmail.com    |



`INNER JOIN`

Most commonly used join - matches a column value in one table to that in another to map their relationship

Often use a primary key and foreign key to do the mapping

```sql
SELECT
p.first_name,
p.last_name,
e.email_address
FROM person p
INNER JOIN email_address e
ON p.person_guid = e.person_guid ;
```

will exclude rows where there is no match (will exclude NULL values)

| First Name | Last Name | Email Address        |
| ---------- | --------- | -------------------- |
| Jon        | Smith     | jonsmith@gmail.com   |
| Mark       | Presto    | markpresto@gmail.com |



`LEFT OUTER JOIN` - includes all rows from the first table and fills in null for non-matching second table values

```sql
SELECT
p.first_name,
p.last_name,
e.email_address
FROM person p
LEFT OUTER  JOIN email_address e
ON p.person_guid = e.person_guid ;
```

| First Name | Last Name | Email Address        |
| ---------- | --------- | -------------------- |
| Jon        | Smith     | jonsmith@gmail.com   |
| Paul       | Ruby      | NULL                 |
| Mark       | Presto    | markpresto@gmail.com |



`RIGHT OUTER JOIN` - includes all rows from the second table and fills in null for non-matching first table values

```sql
SELECT
p.first_name,
p.last_name,
e.email_address
FROM person p
RIGHT OUTER  JOIN email_address e
ON p.person_guid = e.person_guid ;
```

| First Name | Last Name | Email Address        |
| ---------- | --------- | -------------------- |
| Jon        | Smith     | jonsmith@gmail.com   |
| Mark       | Presto    | markpresto@gmail.com |
| NULL       | NULL      | someone@gmail.com    |



`FULL OUTER JOIN` - includes all rows from either table even if there is no match for that row

```sql
SELECT
p.first_name,
p.last_name,
e.email_address
FROM person p
FULL OUTER  JOIN email_address e
ON p.person_guid = e.person_guid ;
```

| First Name | Last Name | Email Address        |
| ---------- | --------- | -------------------- |
| Jon        | Smith     | jonsmith@gmail.com   |
| Paul       | Ruby      | NULL                 |
| Mark       | Presto    | markpresto@gmail.com |
| NULL       | NULL      | someone@gmail.com    |



`UNION` is a sort of join that allows you to combine tables/result sets into one table/result set with all rows

If there may be repeated rows, you can add DISTINCT

```sql
SELECT -- our LEFT OUTER JOIN
p.first_name,
p.last_name,
e.email_address
FROM person p
LEFT OUTER  JOIN email_address e
ON p.person_guid = e.person_guid ;

UNION DISTINCT

SELECT -- our RIGHT OUTER JOIN
p.first_name,
p.last_name,
e.email_address
FROM person p
RIGHT OUTER  JOIN email_address e
ON p.person_guid = e.person_guid ;
```

this returns the same as our `FULL OUTER JOIN`



`SELF JOIN`

Used to JOIN a table on itself

Odd but sometimes useful when table contains hierarchical data





## INSERT

`INSERT`

Can only insert into one table

```sql
INSERT INTO <table> (<column>, <column>) VALUES ('value', 'value') ;
```

```sql
INSERT INTO person (first_name, last_name) VALUES ('Guy', 'Richi') ;
```

notice how we didn't specify the `Key` as it is auto generated



Can insert multiple rows

With multiple values lists..

```sql
INSERT INTO person p
(p.first_name, p.last_name)
VALUES
('Guy', 'Richi'),
('Jack', 'Oven')  ;
```



With a SELECT statement from another table..

```sql
INSERT INTO person p
SELECT * FROM person_old po
WHERE po.person_id < 300 ;
```



## UPDATE

`UPDATE`

Can only update one table

```sql
UPDATE <table> SET <column> = 'value' WHERE <column> = 'value' ;
```

```sql
UPDATE person p
SET p.last_name = 'Smith'
WHERE p.person_id = 1 ;
```



Can update multiple columns

```sql
UPDATE person p
SET
p.first_name = 'John',
p.last_name = 'Smith'
WHERE p.person_id = 1 ;
```





## DELETE

`DELETE` 

Can only delete from one table

```sql
DELETE FROM <table> WHERE <column> = 'value' ;
```

```sql
DELETE FROM person p
WHERE p.person_id = 2 ;
```











ok