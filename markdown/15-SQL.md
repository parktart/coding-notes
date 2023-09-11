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

SQL will be used to make the queries



## Basic SQL Syntax



`SELECT` retrieve one or more columns? from one or more tables

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





`INSERT` add one or more rows into a single table

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

- Column names should not be repeated inside a database (he prefixes all column names with the table name)



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

Here `'Hi', 'Bye'` is the called the **select list**



We normall list columns we want to select in the **select list**

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

1. WHERE Clause
2. DISTINCT Qualifier



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



#### WHERE Clause





















ok