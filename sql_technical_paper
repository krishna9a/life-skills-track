# SQL

## Manipulation

### Column Constraints

Column constraints define rules for individual columns:

- **PRIMARY KEY**: Uniquely identifies each row.
- **UNIQUE**: Ensures each value in the column is different.
- **NOT NULL**: Requires the column to have a value.
- **DEFAULT**: Assigns a default value when none is provided.

For example:
```sql
CREATE TABLE student (
    id INTEGER PRIMARY KEY,
    name TEXT UNIQUE,
    grade INTEGER NOT NULL,
    age INTEGER DEFAULT 10
);
```

- A table can have only one PRIMARY KEY column, but multiple UNIQUE columns.

### CREATE TABLE Statement

The CREATE TABLE statement creates a new table in a database, allowing you to define table and column names.

For example:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
```

### INSERT Statement

The INSERT INTO statement adds a new record to a table. It can insert values in order or by specifying column names.

Example - Insert in order:
```sql
INSERT INTO table_name
VALUES (value1, value2);
```

Example - Insert by name:
```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### ALTER TABLE Statement

The ALTER TABLE statement modifies columns in an existing table, allowing you to add a new column.

For example:
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

### DELETE Statement

The DELETE statement removes records from a table based on a specified condition. If no condition is given, all records are deleted.

For example:
```sql
DELETE FROM table_name
WHERE some_column = some_value;
```

### UPDATE Statement

The UPDATE statement edits records in a table, using a SET clause to specify the column to update and a WHERE clause to filter the records.

For example:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE some_column = some_value;
```

## Queries

### AND Operator

The AND operator combines conditions, requiring records to meet both conditions to be included in the result set.

Example: This query matches cars that are blue and made after 2014.
```sql
SELECT model
FROM cars
WHERE color = 'blue'
AND year > 2014;
```

### AS Clause

The AS clause aliases columns or tables, allowing you to rename them in the result set.

Example: This query renames the `name` column to `movie_title`.
```sql
SELECT name AS 'movie_title'
FROM movies;
```

### OR Operator

The OR operator combines conditions, including records that match either condition.

Example: This query matches customers from 'CA' or 'NY'.
```sql
SELECT name
FROM customers
WHERE state = 'CA'
OR state = 'NY';
```

### % Wildcard

The % wildcard is used in a LIKE pattern to match zero or more unspecified characters.

Example: This query matches movies starting with "The," followed by any characters.
```sql
SELECT name
FROM movies
WHERE name LIKE 'The%';
```

### SELECT Statement

The SELECT * statement retrieves all columns and records from a table.

Example: This query fetches all columns and records from the `movies` table.
```sql
SELECT *
FROM movies;
```

### _ Wildcard

The _ wildcard matches any single unspecified character in a LIKE pattern.

Example: This query matches movies with a single character followed by "ove."
```sql
SELECT name
FROM movies
WHERE name LIKE '_ove';
```

### ORDER BY Clause

The ORDER BY clause sorts the result set by a specific column, either alphabetically or numerically, in ascending (ASC) or descending (DESC) order.

Example:
```sql
SELECT *
FROM contacts
ORDER BY birth_date DESC;
```

### LIKE Operator

The LIKE operator is used in a WHERE clause to match a specified pattern.

Example: This query matches movies starting with "Star" in their titles.
```sql
SELECT name
FROM movies
WHERE name LIKE 'Star%';
```

### DISTINCT Clause

The DISTINCT query selects unique values from a column.

Example: For a table with city values Chicago, Madison, Boston, Madison, and Denver, this query returns:
```
Chicago
Madison
Boston
Denver
```

```sql
SELECT DISTINCT city
FROM contact_details;
```

### BETWEEN Operator

The BETWEEN operator filters records based on a range of values, whether text, numbers, or dates.

Example: This query matches movies made between 1980 and 1990.
```sql
SELECT *
FROM movies
WHERE year BETWEEN 1980 AND 1990;
```

### LIMIT Clause

The LIMIT clause restricts the result set to a specified number of rows.

Example: This query limits the result set to 5 rows.
```sql
SELECT *
FROM movies
LIMIT 5;
```

### NULL Values

Records with NULL values in columns can be matched or excluded using IS NULL and IS NOT NULL operators in combination with the WHERE clause.

Example: This query matches records where the `address` has a value.
```sql
SELECT address
FROM records
WHERE address IS NOT NULL;
```

### WHERE Clause

The WHERE clause filters records that meet a specific condition.

Example: This query selects records with `pub_year` equal to 2017.
```sql
SELECT title
FROM library
WHERE pub_year = 2017;
```

## Aggregate Functions

### Column References

GROUP BY and ORDER BY clauses can reference selected columns by their order in the SELECT statement. The following query counts movies per rating:

```sql
SELECT COUNT(*) AS 'total_movies',
       rating
FROM movies
GROUP BY 2
ORDER BY 1;
```

### SUM() Aggregate Function

The SUM() function totals values in a column.

Example:
```sql
SELECT SUM(salary)
FROM salary_disbursement;
```

### MAX() Aggregate Function

The MAX() function returns the largest value in a column.

Example:
```sql
SELECT MAX(amount)
FROM transactions;
```

### COUNT() Aggregate Function

The COUNT() function counts the number of rows matching specified criteria.

Example: To count employees with less than 5 years of experience.
```sql
SELECT COUNT(*)
FROM employees
WHERE experience < 5;
```

### GROUP BY Clause

The GROUP BY clause groups records in a result set by identical values in one or more columns, often used with aggregate functions.

Example: Counting movies per rating.
```sql
SELECT rating,
       COUNT(*)
FROM movies
GROUP BY rating;
```

### MIN() Aggregate Function

The MIN() function returns the smallest value in a column.

Example: Finding the smallest `amount` value in transactions.
```sql
SELECT MIN(amount)
FROM transactions;
```

### AVG() Aggregate Function

The AVG() function calculates the average value in a column.

Example: Calculating the average salary of employees with less than 5 years of experience.
```sql
SELECT AVG(salary)
FROM employees
WHERE experience < 5;
```

### HAVING Clause

The HAVING clause filters result set groups based on aggregate properties, often used with GROUP BY and aggregate functions.

Example: Selecting records from years with more than 5 movies.
```sql
SELECT year,
       COUNT(*)
FROM movies
GROUP BY year
HAVING COUNT(*) > 5;
```

### ROUND()

 Function

The ROUND() function rounds a number to a specified decimal place, often used with aggregate functions.

Example: Calculating the average rating of movies from 2015 rounded to 2 decimal places.
```sql
SELECT year,
       ROUND(AVG(rating), 2)
FROM movies
WHERE year = 2015;
```

## Multiple Tables

### Outer Join

An outer join combines rows from different tables, even if the join condition isn't met. A LEFT JOIN returns all rows from the left table and fills columns from the right table with NULL if there's no match.

Example:
```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

### WITH Clause

The WITH clause stores query results in temporary tables with aliases. Multiple temporary tables can be defined in one query.

Example:
```sql
WITH temporary_movies AS (
    SELECT *
    FROM movies
)
SELECT *
FROM temporary_movies
WHERE year BETWEEN 2000 AND 2020;
```

### UNION Clause

The UNION clause combines results from multiple SELECT statements and removes duplicates.

Example: Combining data from two tables and eliminating duplicates.
```sql
SELECT name
FROM first_names
UNION
SELECT name
FROM last_names;
```

### CROSS JOIN Clause

The CROSS JOIN clause combines each row from one table with each row from another, creating all possible combinations.

Example:
```sql
SELECT shirts.shirt_color,
       pants.pants_color
FROM shirts
CROSS JOIN pants;
```

### Foreign Key

A foreign key is a reference in one table to the primary key of another, maintaining relationships between tables to track related data.

### Primary Key

A primary key uniquely identifies each record in a SQL table and cannot have NULL values or duplicate values.

### Inner Join

The INNER JOIN returns results matching the join condition, combining records from multiple tables based on common column values specified using the ON clause.

Example:
```sql
SELECT *
FROM books
JOIN authors
ON books.author_id = authors.id;
```


For more details, you can refer to the [Codecademy SQL Cheatsheet](https://www.codecademy.com/learn/learn-sql/modules/learn-sql-aggregate-functions/cheatsheet).
