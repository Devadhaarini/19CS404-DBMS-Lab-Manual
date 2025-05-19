# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
![image](https://github.com/user-attachments/assets/01118e23-5041-4201-984f-a651f29de46a)


```sql
SELECT 
medication_id AS medic,
medication_name,
dosage
FROM Medications
WHERE CAST(REPLACE(dosage,'mg','') AS INTEGER)=(SELECT MAX(CAST(REPLACE(dosage,'mg','') AS INTEGER))
FROM Medications);
```

**Output:**
![image](https://github.com/user-attachments/assets/24de98fa-a1d3-476d-9d17-a2de6a4fb6e3)


**Question 2**
![image](https://github.com/user-attachments/assets/45ebc271-e33c-48a7-825b-b68b1ed56cdd)


```sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';
```

**Output:**
![image](https://github.com/user-attachments/assets/3e476495-e3cb-4943-b3a6-5aee1400f6e4)


**Question 3**
![image](https://github.com/user-attachments/assets/5953db22-eed0-4d5f-9e14-55436abad0d8)


```sql
SELECT student_name,grade
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```

**Output:**
![image](https://github.com/user-attachments/assets/1309fa26-0b90-4091-8bd6-beadab376474)


**Question 4**
![image](https://github.com/user-attachments/assets/540ab909-96d0-476c-95ab-ddd7c8d6af51)


```sql
SELECT *
FROM customer
WHERE city <>(
SELECT
city
FROM customer
WHERE id=(SELECT MAX(id) FROM customer));
```

**Output:**
![image](https://github.com/user-attachments/assets/cbd41ab9-e5ad-4707-819e-e4cbd8aa699c)


**Question 5**
![image](https://github.com/user-attachments/assets/f5bc1211-7abb-447d-a998-ea34c1f6825e)


```sql
SELECT 
name
FROM customer
WHERE phone IN(
SELECT phone
FROM customer
GROUP BY phone
HAVING COUNT(*)=1)
```

**Output:**
![image](https://github.com/user-attachments/assets/cbb94775-a3ca-419c-8e03-2e514709accc)


**Question 6**
![image](https://github.com/user-attachments/assets/801b8111-a516-489e-b974-b746ba444b68)


```sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MAX(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```

**Output:**
![image](https://github.com/user-attachments/assets/8a20aa81-9ea8-46ac-b385-e2fa0322c502)


**Question 7**
![image](https://github.com/user-attachments/assets/036398ea-e3e1-4149-9b02-55c57e76c488)


```sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';
```

**Output:**
![image](https://github.com/user-attachments/assets/4b9ab562-3ab0-4969-85c8-5c3a798509e6)


**Question 8**
![image](https://github.com/user-attachments/assets/9904fe0c-620b-463c-a55c-a38894fc072c)


```sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);
```

**Output:**
![image](https://github.com/user-attachments/assets/ad0ecb1a-957f-4535-9839-e6e331a7b40a)


**Question 9**
![image](https://github.com/user-attachments/assets/fcc05d20-0230-4f5b-98bb-25e508fe1510)


```sql
SELECT * 
FROM Orders
WHERE salesman_id IN(
SELECT
salesman_id
FROM Orders
WHERE customer_id='3007');
```

**Output:**
![image](https://github.com/user-attachments/assets/0a970626-1941-411d-8f5f-4360eb15f5fc)


**Question 10**
![image](https://github.com/user-attachments/assets/1e9e6dcb-6b89-4ae1-8d2a-e4b6d6e1ed61)


```sql
SELECT *
FROM Employee
WHERE age<(SELECT AVG(age) FROM Employee WHERE income>250000);
```

**Output:**
![image](https://github.com/user-attachments/assets/33c56fc3-7b8d-44b4-ad24-56e9f8163fb1)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
