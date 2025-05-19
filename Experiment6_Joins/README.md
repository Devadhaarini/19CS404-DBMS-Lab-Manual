# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
![image](https://github.com/user-attachments/assets/851260db-a9ac-4fd2-abac-01b011fc0bbd)

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;
```

**Output:**
![image](https://github.com/user-attachments/assets/e535ac31-76b6-4fbd-bf5a-72e39f3ac8c6)

**Question 2**
![image](https://github.com/user-attachments/assets/ec113dda-6686-4a98-8a16-6156b98c146b)


```sql
SELECT DISTINCT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id AND o.purch_amt < 100
WHERE o.purch_amt IS NOT NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/64dc9cec-d4a6-453b-90ee-750cfd0a2b62)


**Question 3**
![image](https://github.com/user-attachments/assets/f94d3def-4381-49c6-b0df-2e8d0b54315f)

```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman AS s
INNER JOIN 
    customer AS c
ON 
    s.city = c.city;
```

**Output:**
![image](https://github.com/user-attachments/assets/eb109ed3-d459-4149-a016-709a25d8269b)


**Question 4**
![image](https://github.com/user-attachments/assets/b069e358-fdc0-49d4-bd9a-9ab475d91952)


```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**
![image](https://github.com/user-attachments/assets/8833ab64-0516-434a-b7fd-f6446fbe4de9)


**Question 5**
![image](https://github.com/user-attachments/assets/ce5aa87d-db28-4114-bf7c-e20adf7f8b47)


```sql
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.date_of_birth > '1990-01-01';
```

**Output:**
![image](https://github.com/user-attachments/assets/e0a934e2-2a88-416c-b63e-0b7683d27656)


**Question 6**
![image](https://github.com/user-attachments/assets/94201d1d-7d30-4aa3-a9c0-51132c105d7b)


```sql
SELECT 
    c.cust_name, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;
```

**Output:**
![image](https://github.com/user-attachments/assets/53d145e0-5bc0-434e-a7c3-535042cf712e)


**Question 7**
![image](https://github.com/user-attachments/assets/3360f571-5729-4464-8d11-a380f7fa4165)


```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date > '2012-08-17';
```

**Output:**
![image](https://github.com/user-attachments/assets/519d8a7b-27bb-444e-8811-660e93946e7e)


**Question 8**
![image](https://github.com/user-attachments/assets/2ca0ce74-9c55-4dff-bcb7-c2081e9511ea)


```sql
SELECT 
    p.date_of_birth, 
    a.*
FROM 
    patients AS p
INNER JOIN 
    appointments AS a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';
```

**Output:**
![image](https://github.com/user-attachments/assets/7d1793c9-7057-496a-840c-babfbf59f883)


**Question 9**
![image](https://github.com/user-attachments/assets/3743ad31-c3bb-4691-86fd-a36e3904a5f6)


```sql
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray' AND t.result = 'Normal';
```

**Output:**
![image](https://github.com/user-attachments/assets/99d649e1-f9c9-4489-a9eb-5cf929a23255)


**Question 10**
![image](https://github.com/user-attachments/assets/d904a2f8-bd5b-4fda-91e3-d417baf1fff4)


```sql
SELECT 
    patients.first_name AS patient_name,
    doctors.first_name AS doctor_name
FROM 
    patients
INNER JOIN 
    doctors ON patients.doctor_id = doctors.doctor_id
WHERE 
    patients.discharge_date IS NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/6c78d180-5fb6-437d-8fbf-2e2195d3d0d0)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
