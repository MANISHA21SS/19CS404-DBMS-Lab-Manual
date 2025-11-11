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
--
<img width="1288" height="627" alt="Screenshot 2025-11-11 192258" src="https://github.com/user-attachments/assets/52fe6b91-c6d2-4802-97af-f9693a967d22" />


```
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;
```

**Output:**

<img width="1280" height="411" alt="Screenshot 2025-11-11 192335" src="https://github.com/user-attachments/assets/31c813b2-a67a-4369-9dce-4450adb56643" />


**Question 2**
---
<img width="1207" height="752" alt="Screenshot 2025-11-11 192357" src="https://github.com/user-attachments/assets/bcfb63f8-3387-4b9c-8aad-1bee72fde312" />


```
SELECT *
FROM customer
WHERE customer_id = (
    (SELECT salesman_id FROM salesman WHERE name = 'Mc Lyon') - 2001
);

```

**Output:**

<img width="1282" height="396" alt="Screenshot 2025-11-11 192429" src="https://github.com/user-attachments/assets/3fd615e5-c2e4-4653-9e5c-8147423c3d3a" />


**Question 3**
---
<img width="1209" height="502" alt="Screenshot 2025-11-11 192449" src="https://github.com/user-attachments/assets/0eca7b89-3f98-46d5-8393-2ee50450441d" />


```
SELECT *
FROM Medications
WHERE dosage = (
    SELECT MAX(dosage)
    FROM Medications
);

```

**Output:**

<img width="1287" height="488" alt="Screenshot 2025-11-11 192520" src="https://github.com/user-attachments/assets/54c073b2-755e-46bc-a2e6-311d87b75bf8" />


**Question 4**
---
<img width="1233" height="680" alt="Screenshot 2025-11-11 192541" src="https://github.com/user-attachments/assets/6caca9ee-79b2-4060-bef0-c75cd07d9680" />


```
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**

<img width="1285" height="543" alt="Screenshot 2025-11-11 192612" src="https://github.com/user-attachments/assets/8c4a2cc7-60a6-473f-a6ae-c5095bc0922c" />


**Question 5**
---
<img width="1270" height="505" alt="Screenshot 2025-11-11 192633" src="https://github.com/user-attachments/assets/92431c78-1146-4a70-b1c0-82c6dc3eaf71" />


```
SELECT grade, COUNT(*)
FROM customer
WHERE city = 'New York'
  AND grade > (
      SELECT AVG(grade)
      FROM customer
      WHERE city = 'New York'
  )
GROUP BY grade;

```

**Output:**

<img width="1282" height="414" alt="Screenshot 2025-11-11 192704" src="https://github.com/user-attachments/assets/62f1f29a-8466-421f-9632-0fa669af1a5e" />


**Question 6**
---
<img width="1260" height="454" alt="Screenshot 2025-11-11 192723" src="https://github.com/user-attachments/assets/ec096cb1-d3a4-4711-830e-ab526e342026" />


```
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

<img width="1289" height="473" alt="Screenshot 2025-11-11 192752" src="https://github.com/user-attachments/assets/44c5ba44-8088-45ad-a745-7167149fa466" />


**Question 7**
---
<img width="1283" height="657" alt="Screenshot 2025-11-11 192812" src="https://github.com/user-attachments/assets/5b41e849-ab31-49b0-9371-a5c2be2241b3" />


```
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);

```

**Output:**

<img width="1281" height="600" alt="Screenshot 2025-11-11 192842" src="https://github.com/user-attachments/assets/3dd396b8-a153-43e0-b402-98aa258ecc9b" />


**Question 8**
---
<img width="1262" height="765" alt="Screenshot 2025-11-11 192902" src="https://github.com/user-attachments/assets/4675ed91-3466-42a0-93e6-e747f531a53a" />


```
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

<img width="1289" height="667" alt="Screenshot 2025-11-11 192934" src="https://github.com/user-attachments/assets/5d6db2c8-47cf-4279-820d-5b236b3627b4" />

**Question 9**
---
<img width="1264" height="655" alt="Screenshot 2025-11-11 192953" src="https://github.com/user-attachments/assets/08291d8a-b2b0-4471-a586-f76b759997bd" />


```
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="1288" height="508" alt="Screenshot 2025-11-11 193029" src="https://github.com/user-attachments/assets/096e42ee-ee50-4b1a-80c6-cc31a67f629c" />


**Question 10**
---
<img width="1254" height="759" alt="Screenshot 2025-11-11 193049" src="https://github.com/user-attachments/assets/105ea743-7c37-4dcf-a1a8-ba81ed5d633c" />


```
SELECT o."order_no", o."purch_amt", o."order_date", o."customer_id", o."salesman_id"
FROM "orders" o
JOIN "salesman" s
ON o."salesman_id" = s."salesman_id"
WHERE s."city" = 'London';

```

**Output:**

<img width="1272" height="646" alt="Screenshot 2025-11-11 193120" src="https://github.com/user-attachments/assets/3b46fe63-5614-4ceb-89b9-3e4e199bf24e" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
