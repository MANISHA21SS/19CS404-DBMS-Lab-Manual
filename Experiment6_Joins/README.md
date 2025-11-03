<img width="1462" height="830" alt="Screenshot 2025-11-03 152856" src="https://github.com/user-attachments/assets/eda9afe5-e9c1-449b-a4ff-929dba0ff2b7" /># Experiment 6: Joins

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

<img width="1462" height="830" alt="Screenshot 2025-11-03 152856" src="https://github.com/user-attachments/assets/8955f3bb-3a58-40ec-aabe-ff4273d84ca7" />
<img width="1286" height="713" alt="Screenshot 2025-11-03 152916" src="https://github.com/user-attachments/assets/ac892750-b86c-4945-b6a0-d6ce61979081" />


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

<img width="1264" height="826" alt="Screenshot 2025-11-03 152932" src="https://github.com/user-attachments/assets/ed896883-5fd1-4c1c-8a08-5df02dbde470" />


**Question 2**
---
<img width="1463" height="750" alt="Screenshot 2025-11-03 153347" src="https://github.com/user-attachments/assets/66a47142-0501-49ef-98c5-407f03e809d6" />


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

<img width="1281" height="725" alt="Screenshot 2025-11-03 153439" src="https://github.com/user-attachments/assets/df0d341f-44a0-4f34-9300-b66eadfa1a84" />


**Question 3**
---
<img width="1480" height="840" alt="Screenshot 2025-11-03 153506" src="https://github.com/user-attachments/assets/8ed09aa7-1c3a-43af-a49f-7f0d590eeb2e" />


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
<img width="1280" height="625" alt="Screenshot 2025-11-03 153543" src="https://github.com/user-attachments/assets/0b9f9091-7445-4719-9fef-5ce705264625" />


**Question 4**
---
<img width="1466" height="762" alt="Screenshot 2025-11-03 153604" src="https://github.com/user-attachments/assets/3739a0e7-ed4b-439d-a7f7-59b3169cfcfb" />


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

<img width="1300" height="625" alt="Screenshot 2025-11-03 153635" src="https://github.com/user-attachments/assets/00f976aa-6e94-45f1-9476-1afc8b5bf20a" />


**Question 5**
---
<img width="1469" height="772" alt="Screenshot 2025-11-03 153727" src="https://github.com/user-attachments/assets/49c26f62-29c3-4e2c-8869-b9857a08a13d" />


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

<img width="1256" height="655" alt="Screenshot 2025-11-03 153815" src="https://github.com/user-attachments/assets/7ed5a1b6-ccdc-4a88-8277-ed130fd201f8" />


**Question 6**
---
<img width="1443" height="420" alt="Screenshot 2025-11-03 153833" src="https://github.com/user-attachments/assets/e6981b0e-862d-470d-81a7-89c03d9af0e7" />


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

<img width="1281" height="563" alt="Screenshot 2025-11-03 153906" src="https://github.com/user-attachments/assets/66ca2cfe-823b-4e23-a04b-fd7978f4b912" />


**Question 7**
---
<img width="1463" height="645" alt="Screenshot 2025-11-03 153929" src="https://github.com/user-attachments/assets/f2947a7b-9882-4d03-b740-46902ee91cb6" />
<img width="1351" height="377" alt="Screenshot 2025-11-03 153947" src="https://github.com/user-attachments/assets/f3cddb2f-6a91-4a16-ae3d-50823c7ce567" />


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
<img width="1248" height="829" alt="Screenshot 2025-11-03 154024" src="https://github.com/user-attachments/assets/46c7d62f-b0d3-4767-bb35-ff99f57c9167" />


**Question 8**
---
<img width="1452" height="768" alt="Screenshot 2025-11-03 154047" src="https://github.com/user-attachments/assets/f3dd2394-b70b-48a3-a1e1-aee67874e75c" />
<img width="1382" height="469" alt="Screenshot 2025-11-03 154101" src="https://github.com/user-attachments/assets/898a5d04-135b-41b1-9cf4-6497580cf5c4" />


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

<img width="1261" height="842" alt="Screenshot 2025-11-03 154145" src="https://github.com/user-attachments/assets/4731c4c2-e81c-4c72-af0c-abdff237ecbd" />

**Question 9**
---
<img width="1459" height="629" alt="Screenshot 2025-11-03 154212" src="https://github.com/user-attachments/assets/3d27332e-6772-4cc3-ade0-9634d1a1ef57" />
<img width="1400" height="340" alt="Screenshot 2025-11-03 154231" src="https://github.com/user-attachments/assets/33d06d26-4ee9-479d-b639-e1e8c690fbe7" />


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
<img width="1281" height="815" alt="Screenshot 2025-11-03 154305" src="https://github.com/user-attachments/assets/035412e5-0af6-4c33-b392-222fd3af660d" />


**Question 10**
---
<img width="1471" height="469" alt="Screenshot 2025-11-03 154325" src="https://github.com/user-attachments/assets/c6755399-c75f-49f7-9779-cde00e195018" />


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

<img width="1301" height="583" alt="Screenshot 2025-11-03 154357" src="https://github.com/user-attachments/assets/02e6ee6d-7981-4916-bc71-faa593e165a8" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
