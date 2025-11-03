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
--
<img width="1441" height="823" alt="Screenshot 2025-11-03 154600" src="https://github.com/user-attachments/assets/32d18281-42b2-44cb-89f0-6605ab969a02" />


```
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1264" height="826" alt="Screenshot 2025-11-03 152932" src="https://github.com/user-attachments/assets/3e37bee0-9050-4027-b097-6a1fd87cbd70" />


**Question 2**
---
<img width="1463" height="750" alt="Screenshot 2025-11-03 153347" src="https://github.com/user-attachments/assets/013cf3a7-1381-4e08-a7e9-16fd9dd41599" />


```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_result t
ON 
    p.patient_id = t.patient_id
WHERE 
    (t.test_name = 'Blood Test' OR t.test_name = 'Blood Pressure')
    AND t.result NOT LIKE '%Normal%';

```

**Output:**
<img width="1281" height="725" alt="Screenshot 2025-11-03 153439" src="https://github.com/user-attachments/assets/5b4c20f2-6a95-4b81-aae6-6e006d7ab9d3" />


**Question 3**
---
<img width="1480" height="840" alt="Screenshot 2025-11-03 153506" src="https://github.com/user-attachments/assets/34a58548-59cf-4b8f-9dac-093b86a47889" />


```
SELECT 
    p.admission_date,
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;

```

**Output:**

<img width="1280" height="625" alt="Screenshot 2025-11-03 153543" src="https://github.com/user-attachments/assets/88745d9a-7b82-4231-88b8-e6ac02f6f06e" />


**Question 4**
---
<img width="1466" height="762" alt="Screenshot 2025-11-03 153604" src="https://github.com/user-attachments/assets/babfb55d-4ee1-4a8a-b101-3bb2109bc1e8" />


```
SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id;

```

**Output:**

<img width="1300" height="625" alt="Screenshot 2025-11-03 153635" src="https://github.com/user-attachments/assets/99fab5a5-7661-4a42-b038-b8ef73411e8e" />


**Question 5**
---
<img width="1469" height="772" alt="Screenshot 2025-11-03 153727" src="https://github.com/user-attachments/assets/3ee59177-ca0e-4a4f-88f1-2ec49e2549b2" />


```
SELECT 
    p.admission_date,
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;

```

**Output:**

<img width="1256" height="655" alt="Screenshot 2025-11-03 153815" src="https://github.com/user-attachments/assets/ae62e35e-dfcf-4439-8045-acfd4da89c2b" />


**Question 6**
---
<img width="1443" height="420" alt="Screenshot 2025-11-03 153833" src="https://github.com/user-attachments/assets/b44a8c92-3e96-47f8-9c41-2def1c85cdf4" />


```
SELECT 
    c.cust_name
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt < 100;

```

**Output:**

<img width="1281" height="563" alt="Screenshot 2025-11-03 153906" src="https://github.com/user-attachments/assets/188088f2-3199-48b8-9446-423b47e295ee" />


**Question 7**
---
<img width="1463" height="645" alt="Screenshot 2025-11-03 153929" src="https://github.com/user-attachments/assets/7ae98eee-593f-4917-a1cd-1d7fe92ab273" />
<img width="1351" height="377" alt="Screenshot 2025-11-03 153947" src="https://github.com/user-attachments/assets/3746db5d-00b2-4be8-8f88-f738ca5c351c" />


```
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**
<img width="1248" height="829" alt="Screenshot 2025-11-03 154024" src="https://github.com/user-attachments/assets/b0b09993-3aa3-42b9-a0bf-09276c0f359d" />


**Question 8**
---
<img width="1452" height="768" alt="Screenshot 2025-11-03 154047" src="https://github.com/user-attachments/assets/a92a2fea-69a6-4525-aa25-443145237d4b" />
<img width="1382" height="469" alt="Screenshot 2025-11-03 154101" src="https://github.com/user-attachments/assets/0ceef92f-4e8d-4497-8ccc-8c0dec37c659" />


```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;

```

**Output:**
<img width="1261" height="842" alt="Screenshot 2025-11-03 154145" src="https://github.com/user-attachments/assets/03222f22-a017-4825-ac5b-bba09e7ae520" />


**Question 9**
---
<img width="1459" height="629" alt="Screenshot 2025-11-03 154212" src="https://github.com/user-attachments/assets/a60d8aca-0924-426b-ba7b-7fc530458a45" />
<img width="1400" height="340" alt="Screenshot 2025-11-03 154231" src="https://github.com/user-attachments/assets/36b21431-ccd2-4373-ab5c-3d7893f7ff81" />


```
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**
<img width="1281" height="815" alt="Screenshot 2025-11-03 154305" src="https://github.com/user-attachments/assets/292ec699-f882-4a7f-9cad-0de419369669" />


**Question 10**
---
<img width="1471" height="469" alt="Screenshot 2025-11-03 154325" src="https://github.com/user-attachments/assets/4405fced-992f-405c-906d-ba6be2ad3102" />


```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    c.city = 'London';

```

**Output:**

<img width="1301" height="583" alt="Screenshot 2025-11-03 154357" src="https://github.com/user-attachments/assets/d592a87e-0af1-4062-9048-728520e8e140" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
