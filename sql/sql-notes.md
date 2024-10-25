
# SQL Commands and Concepts Guide

This guide covers SQL basics, advanced commands, functions, joins, and key concepts to help manage and manipulate databases effectively.

---

## 1. SQL Basics

### Show Columns from a Table
Display the columns in a specified table.
```sql
SHOW COLUMNS FROM table_name;
```

### Get Table Schema Definition
Retrieve the structure and definition of a table.
```sql
DESC table_name;
```

### Sorting the Result
Order results by specific columns in ascending or descending order.
```sql
SELECT * FROM table_name ORDER BY first_column DESC, second_column ASC;
```

### Case-Sensitive Ordering
Order rows with case sensitivity.
```sql
SELECT * FROM table_name ORDER BY BINARY first_column;
```

### Sort by Casting
Sort by converting data types (e.g., casting to CHAR).
```sql
SELECT * FROM table_name ORDER BY CAST(first_column AS CHAR);
```

### Alter Table Column
Modify column properties in a table.
```sql
ALTER TABLE table_name CHANGE first_column fcolumn VARCHAR(120);
```

### Indexing Table
Add an index to improve search speed.
```sql
ALTER TABLE table_name ADD INDEX colOneIndex (first_column);
ALTER TABLE table_name ADD INDEX colOneIndexWith10Chars (first_column(10));
```

### Display Indexes
Show the index information of a table.
```sql
SHOW INDEX FROM table_name;
```

---

## 2. Table Aliasing and DISTINCT Rows

### Table Alias
Create temporary names for columns or tables.
```sql
SELECT CONCAT(first_column, ' ', second_column) AS complete_column FROM table_name ORDER BY complete_column;
```

### DISTINCT Rows
Remove duplicates in result rows.
```sql
SELECT DISTINCT first_column FROM table_name;
SELECT DISTINCT first_column, second_column FROM table_name;
```

---

## 3. Aggregate Functions

Perform calculations on a set of values:
- **COUNT**: Counts total rows.
- **SUM**: Adds values.
- **AVG**: Averages values.
- **MAX/MIN**: Retrieves highest/lowest value.

```sql
SELECT COUNT(*) FROM table_name;
SELECT SUM(first_column) FROM table_name;
SELECT AVG(first_column) FROM table_name;
SELECT MAX(first_column), MIN(first_column) FROM table_name;
```

---

## 4. GROUP BY

`GROUP BY` organizes data by unique values in a specified column. It is evaluated after `FROM` and `WHERE`, but before `ORDER BY`.

```sql
SELECT first_column, COUNT(*) FROM table_name GROUP BY first_column;
SELECT first_column, AVG(quantity_column) FROM table_name GROUP BY first_column;
```

---

## 5. HAVING Clause

`HAVING` filters groups in `GROUP BY` results based on aggregate conditions.

```sql
SELECT first_column, AVG(quantity_column) AS avgQuantity FROM table_name GROUP BY first_column HAVING avgQuantity > 100;
```

---

## 6. JOINS

Joins combine rows from different tables:
- **Inner Join**
- **Left Outer Join**
- **Right Outer Join**
- **Full Outer Join**
- **Self Join**

### INNER JOIN Example
```sql
SELECT tab1Col1, tab1Col2, tab2Col1
FROM table_one 
INNER JOIN table_two ON table_one.Id = table_two.relatedId;
```

---

## 7. UNION

Combine results of two queries into one, without duplicates (use `UNION ALL` to include duplicates).

```sql
SELECT tab1Col1 FROM table_one 
UNION 
SELECT tab1Col2 FROM table_one;
```

---

## 8. SQL Functions

Functions for data manipulation:

- **DISTINCT & MOD**
  ```sql
  SELECT DISTINCT city FROM STATION WHERE MOD(ID,2)=0;
  ```

- **LIKE**
  ```sql
  SELECT * FROM movies WHERE title LIKE '%toy%';
  SELECT * FROM movies WHERE director LIKE '%John%';
  ```

- **BETWEEN**
  ```sql
  SELECT * FROM movies WHERE year BETWEEN 2000 AND 2010;
  SELECT * FROM movies WHERE year NOT BETWEEN 2000 AND 2010;
  ```

- **Mathematical Functions** (`SQRT`, `POWER`, `ABS`, `ROUND`, `CEIL`)
  ```sql
  SELECT SQRT(36), POWER(3,2), ABS(b-d), ROUND(sum(long_w),2), CEIL(AVG(REPLACE(SALARY,'0',' ')));
  ```

- **String Functions** (`REPLACE`, `LENGTH`)
  ```sql
  SELECT REPLACE(SALARY, '0', ' '), LENGTH(MAX(city)) FROM station;
  ```

---

## 9. Query Filtering: IN and BETWEEN

**IN** allows selection from a list, while **BETWEEN** selects within a range.

- **IN Example**
  ```sql
  SELECT * FROM Students WHERE ROLL_NO IN (20,21,23);
  ```

- **BETWEEN Example**
  ```sql
  SELECT * FROM Students WHERE ROLL_NO BETWEEN 20 AND 30;
  ```

---

## 10. Data Deletion: DROP, TRUNCATE, DELETE

- **DROP**: Deletes the entire table, non-reversible.
- **TRUNCATE**: Clears all rows in a table without undo option.
- **DELETE**: Removes rows selectively with a WHERE clause.

---

## 11. Keys: PRIMARY KEY and FOREIGN KEY

- **Primary Key**: Unique identifier for table rows; disallows NULLs.
- **Foreign Key**: Establishes link between two tables.

---

## 12. Nested Query and Row Limits

Example of using sub-queries and limiting rows with `ROWNUM`.

```sql
SELECT NAME, TOTAL FROM
(SELECT NAME, SALARY * MONTHS AS TOTAL FROM EMPLOYEE WHERE SALARY > 2000 ORDER BY SALARY) 
WHERE ROWNUM <= 5;
```

---

## 13. Triangle Problem Example

Using `CASE` to classify triangles.

```sql
SELECT CASE WHEN a+b>c AND b+c>a AND a+c>b THEN
            CASE WHEN a=b AND b=c THEN 'Equilateral'
                 WHEN a=b OR b=c OR c=a THEN 'Isosceles'
                 ELSE 'Scalene'
            END
        ELSE 'Not A Triangle'
        END
FROM triangles;
```

---

This guide provides essential SQL commands, functions, and advanced query techniques for data management.
