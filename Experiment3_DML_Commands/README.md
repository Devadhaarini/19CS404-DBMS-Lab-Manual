# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4. Sample table: Surgeries

```sql
DELETE FROM Surgeries
WHERE surgery_id= 3 OR surgery_id= 4;
```

**Output:**
![image](https://github.com/user-attachments/assets/f0f34ced-05e0-414d-be6d-48fba1cc9875)


**Question 2**
Write a SQL query to Retrieve the department name and location concatenated with a comma Table name: dept

```sql
SELECT
dname||', '||loc AS dept_location
FROM dept;
```

**Output:**
![image](https://github.com/user-attachments/assets/033884d3-5031-4974-a811-c4d290e08990)


**Question 3**
Write a query to fetch 5 to 9 records from EmployeeInfo table.

```sql
SELECT *
FROM EmployeeInfo
ORDER BY EmpID
LIMIT 5 OFFSET 4;
```

**Output:**
![image](https://github.com/user-attachments/assets/73f75b53-59ab-47b9-9949-972f8820d719)


**Question 4**
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id. Sample table: customer

```sql
SELECT 
customer_id,
cust_name,
city,
grade,
salesman_id
FROM customer
WHERE city IN ('London') AND grade>200;
```

**Output:**
![image](https://github.com/user-attachments/assets/6a89c26d-fe7e-464d-818b-f6b01603f491)


**Question 5**
Write a SQL query to Delete a Specific Surgery whose ID is 3 Sample table: Surgeries

```sql
DELETE FROM Surgeries
WHERE surgery_id=3;
```

**Output:**
![image](https://github.com/user-attachments/assets/d01eab1e-38f9-4f29-a18c-86e0cb792c89)


**Question 6**
Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.

```sql
SELECT
strftime('%Y',hiredate) AS Year,
strftime('%m',hiredate) AS Month,
strftime('%d',hiredate) AS Day
FROM emp;
```

**Output:**
![image](https://github.com/user-attachments/assets/5d4b44aa-0881-46aa-bf77-0d3ba9feae8f)


**Question 7**
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'. Sample table: Customer

```sql
DELETE FROM Customer
WHERE WORKING_AREA IN ("New York");
```

**Output:**
![image](https://github.com/user-attachments/assets/87984569-2952-4a48-8a71-e98406e64aea)


**Question 8**
For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table. PRODUCTS TABLE

```sql
UPDATE sales
SET sell_price=sell_price+3
WHERE product_id IN(
SELECT product_id
FROM products
WHERE Supplier_id=4
);
```

**Output:**
![image](https://github.com/user-attachments/assets/6224e9f3-c4c9-45a4-9f18-896012acad53)


**Question 9**
Write a SQL query to remove rows from the table 'customer' with the following condition -
1. 'cust_country' must be 'India',
2. 'cus_city' must not be 'Chennai', Sample table: Customer

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY IN ('India') AND CUST_CITY NOT IN ('Chennai');
```

**Output:**
![image](https://github.com/user-attachments/assets/ab998316-d891-44ee-b6b7-8a300feef27a)


**Question 10**
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'. sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price=sell_price+(0.05*sell_price)
WHERE product_id=15 AND sale_date='2023-01-31';
```

**Output:**
![image](https://github.com/user-attachments/assets/ef3ac239-00e0-4b56-a803-06cb6f91b10d)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
