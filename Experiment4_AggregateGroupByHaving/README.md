# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
Write a SQL query to find the total amount of fruits with a unit type of 'LB'. Note: Inventory attribute contains amount of fruits Table: fruits

```sql
SELECT
SUM(inventory) AS total
FROM fruits
WHERE unit LIKE '%LB%';
```

**Output:**
![image](https://github.com/user-attachments/assets/0f367233-c7ad-4303-adf9-9f35e5055a11)


**Question 2**
Write a SQL query to find how many employees have an income greater than 50K? Table: employee

```sql
SELECT
COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```

**Output:**
![image](https://github.com/user-attachments/assets/7551f886-37b8-4be1-99c6-caca7ec6ba15)


**Question 3**
Write a SQL query to find how many employees work in California? Table: employee

```sql
SELECT
COUNT(*) AS employees_in_california
FROM employee
WHERE city='California';
```

**Output:**
![image](https://github.com/user-attachments/assets/9abbb4bd-ec48-492a-9d78-722d0e7c3d5e)


**Question 4**
How many medical records does each doctor have? Sample table:MedicalRecords Table

```sql
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID ASC;
```

**Output:**
![image](https://github.com/user-attachments/assets/84eaa734-3a45-4f2f-99a9-f0f6a602366f)


**Question 5**
What is the average duration of insurance coverage for patients covered by each insurance company? Sample table:Insurance Table

```sql
SELECT
InsuranceCompany,
ABS(AVG(StartDate-EndDate)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**
![image](https://github.com/user-attachments/assets/237fc28f-f93c-40ba-906a-e6d15f324cbd)


**Question 6**
How many medical records are there for each patient? Sample table:MedicalRecords Table

```sql
SELECT
PatientID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
ORDER BY PatientID;
```

**Output:**
![image](https://github.com/user-attachments/assets/41a355dd-a7b0-427d-a9a1-9c8b8e7fa909)


**Question 7**
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000. Sample table: employee

```sqlSELECT
age,
MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income)<1000000;
```

**Output:**
![image](https://github.com/user-attachments/assets/68fbba47-e1bf-4a9f-99f5-9b54317a923a)


**Question 8**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10. Sample table: employee1

```sql
SELECT
jdate,
AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour)<10;
```

**Output:**
![image](https://github.com/user-attachments/assets/faed34c5-7399-4e20-bb75-1f42ce13758d)


**Question 9**
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15. Sample table: products

```sql
SELECT
category_id,
product_name,
MAX(price) AS Price
FROM products
GROUP BY category_id 
HAVING MAX(price)>15;
```

**Output:**
![image](https://github.com/user-attachments/assets/be83f7fc-29a4-4dcf-8637-13d46c52e57e)


**Question 10**
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15. Sample table: products

```sql
SELECT
category_id,
AVG(price) AS 'AVG(Price)'
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;
```

**Output:**
![image](https://github.com/user-attachments/assets/f69a6fde-c554-4ed7-b642-d48047b63ce2)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
