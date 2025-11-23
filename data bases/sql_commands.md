# 📘 SQL Notes 

---

# 1. Creating Database & Tables

## ▶️ Create a new database and select it
```sql
CREATE DATABASE shahda1;
USE shahda1;
```

## ▶️ Create table: employee demographic info
Stores basic personal data for each employee.
```sql
CREATE TABLE Employee_demographics (
    id INT NOT NULL,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    gender VARCHAR(12),
    PRIMARY KEY(id)
);
```
## ▶️ Insert sample data into Employee_demographics
```sql 
INSERT INTO Employee_demographics (id, first_name, last_name, age, gender)
VALUES
(1, "shahda", "mohamed", 19, "female"),
(2, "kareem", "mohamed", 20, "male"),
...
(10,"ahmed", "mohamed", 22, "male", );
```

## ▶️ Create table: employee salary info
Stores salary, job title, and department ID.
```sql 
CREATE TABLE Employee_salary (
    ID INT NOT NULL,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    occupation VARCHAR(50),
    salary INT,
    dept_id INT
);
```
## Insert salary data
```sql
INSERT INTO Employee_salary (ID, first_name, last_name, occupation, salary, dept_id)
VALUES
(1, "shahda", "mohamed", "data analisis",20000, 1),
...
(10,"ahmed", "mohamed", "machine learning", 25000, 5);
```

## ▶️ Create table: departments list
```sql
CREATE TABLE departements (
    departement_id INT NOT NULL,
    depatement_name VARCHAR(50) NOT NULL,
    PRIMARY KEY(departement_id)
);
```

##▶️ Insert department names
```sql
INSERT INTO departements (departement_id, depatement_name)
VALUES
(1, "data analisis"),
(2, "web development"),
...
(5, "machine learning");
```

# 2. SELECT Statements

## ▶️ Select all rows from a table
```sql
SELECT *
FROM employee_demographics;
```

## ▶️ Select specific columns + calculation
(age + 10) * 10 is an expression.
```sql
SELECT first_name, last_name, gender, age, (age + 10) * 10
FROM employee_demographics;
```

## ▶️ Select unique values only (DISTINCT)
```sql
SELECT DISTINCT age 
FROM employee_demographics;
```

# 3. WHERE Clause

## ▶️ Filter rows where salary is greater than 20000

```sql
SELECT * 
FROM employee_salary
WHERE salary > 20000;
```
## ▶️ Filter rows where gender is NOT male
```sql
SELECT * 
FROM employee_demographics
WHERE gender != "male";
```

## ▶️ Pattern search with LIKE

- _ represent 1 character
- % represent 1 chahcter or more
    - _a% → second letter is "a"

```sql
SELECT *
FROM employee_demographics
WHERE first_name LIKE "_a%";
```

# 4. GROUP BY & ORDER BY

## ▶️ Group rows by gender

```sql 
SELECT gender
FROM employee_demographics
GROUP BY gender;
```

## ▶️ Group by two columns: occupation + salary
```sql
SELECT occupation, salary
FROM employee_salary
GROUP BY occupation, salary;
```

## ▶️ Aggregate functions + ORDER BY

- MIN, MAX, COUNT, AVG, and more **search about it**

```sql
SELECT gender, MIN(age), MAX(age), COUNT(age), AVG(age)
FROM employee_demographics
GROUP BY gender
ORDER BY gender;
```

## ▶️ Order rows by first_name descending
```sql 
SELECT *
FROM employee_salary
ORDER BY first_name DESC;
```

## ▶️ Order by column numbers (5 = gender, 4 = age)
```sql
SELECT *
FROM employee_demographics
ORDER BY 5, 4;
```

# 5. HAVING vs WHERE

## ▶️ HAVING filters after GROUP BY (WHERE filters before grouping)
```sql
SELECT occupation, AVG(salary)
FROM employee_salary
WHERE occupation LIKE "web%"
GROUP BY occupation
HAVING AVG(salary) < 20000;
```

# 6. LIMIT & ALIASING

## ▶️ Limit number of returned rows
```sql
SELECT *
FROM employee_salary
LIMIT 3;
```

## ▶️ Create alias (rename a column)
```sql
SELECT first_name, salary * 12 AS "yearly salary"
FROM employee_salary;
```
# 7. JOINs
## ▶️ INNER JOIN: returns only matching rows in both tables
```sql
SELECT *
FROM employee_demographics dem
INNER JOIN employee_salary sal
    ON dem.id = sal.ID;
```

## ▶️ Selecting specific fields from a join
```sql
SELECT dem.id, salary, age, dept_id
FROM employee_demographics dem
INNER JOIN employee_salary sal
    ON dem.id = sal.ID;
```

## ▶️ RIGHT JOIN: returns all rows from right table + matches from left
```sql
SELECT *
FROM employee_demographics
RIGHT JOIN employee_salary
    ON employee_demographics.id = employee_salary.ID;
```
### more resources to study from and learn more: 

- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)

- [youtube playlist](https://www.youtube.com/watch?v=wgRwITQHszU&list=PLUaB-1hjhk8Fq6RBY-3MQ5MCXB5qxb8VA)
