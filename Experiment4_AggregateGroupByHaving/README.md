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
--

<img width="1224" height="590" alt="Screenshot 2025-11-11 000120" src="https://github.com/user-attachments/assets/5a3ebc52-5b34-4f80-908b-4058e3c19e5f" />


```
SELECT Specialty,
        COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty

```

**Output:**

<img width="1227" height="720" alt="Screenshot 2025-11-11 000352" src="https://github.com/user-attachments/assets/f2a81c44-9603-466a-afec-5bf31d19d1f9" />


**Question 2**
---
<img width="1004" height="657" alt="Screenshot 2025-11-11 000430" src="https://github.com/user-attachments/assets/bda25329-b9c1-45ec-9abc-da01e01c9819" />


```
SELECT InsuranceCompany,
        COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1133" height="754" alt="Screenshot 2025-11-11 000527" src="https://github.com/user-attachments/assets/ca26bcaf-841d-4ecc-831a-af19a22547b3" />


**Question 3**
---
<img width="1134" height="653" alt="Screenshot 2025-11-11 000556" src="https://github.com/user-attachments/assets/94201aad-1e0c-4e81-8ae6-b3184b219537" />


```
SELECT
    DATE(AppointmentDateTime)AS AppointmentDate,
    COUNT(*)AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="1181" height="726" alt="Screenshot 2025-11-11 000637" src="https://github.com/user-attachments/assets/fbf32ad4-b94b-4652-83de-4dba021aa039" />


**Question 4**
---

<img width="1147" height="506" alt="Screenshot 2025-11-11 000702" src="https://github.com/user-attachments/assets/b5032b22-278a-4d14-a3c8-215403110d5a" />


```
SELECT name AS Employee_Name,age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;
```

**Output:**

<img width="1209" height="392" alt="Screenshot 2025-11-11 000739" src="https://github.com/user-attachments/assets/39579362-dc0a-4a92-a587-6cc9197a6421" />


**Question 5**
---
<img width="1166" height="558" alt="Screenshot 2025-11-11 000926" src="https://github.com/user-attachments/assets/65bbdf89-7c3f-47f9-9c63-7b4e6a760e0f" />


```
SELECT SUM(inventory) AS total_available_amount
FROM fruits
WHERE price>0.5;
```

**Output:**

<img width="1222" height="385" alt="Screenshot 2025-11-11 001022" src="https://github.com/user-attachments/assets/3b3b9679-c831-48e4-bdbb-4abb3ce713b2" />


**Question 6**
---

<img width="1122" height="497" alt="Screenshot 2025-11-11 001048" src="https://github.com/user-attachments/assets/6fcd83d3-b800-471a-b31d-72b2022c59f6" />


```
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**


<img width="1272" height="386" alt="Screenshot 2025-11-11 001204" src="https://github.com/user-attachments/assets/eadc8a8a-2ffe-483b-8c9b-3235facc5313" />


**Question 7**
---

<img width="1231" height="543" alt="Screenshot 2025-11-11 001229" src="https://github.com/user-attachments/assets/1709e796-b34e-441d-a491-f213422d8a6f" />


```
SELECT category_id,
       SUM (price*category_id) AS Revenue
FROM products
GROUP BY category_id
HAVING SUM(price*category_id)>25;
```

**Output:**


<img width="1221" height="497" alt="Screenshot 2025-11-11 001304" src="https://github.com/user-attachments/assets/b5ec09d8-8cc2-488a-a5ef-63993192ab0b" />


**Question 8**
---

<img width="1221" height="496" alt="Screenshot 2025-11-11 001328" src="https://github.com/user-attachments/assets/f5e9ccfe-5cc2-4b0d-ac82-2ed3657e3748" />


```
SELECT category_id,
      COUNT(*)AS COUNT
FROM products
WHERE category_id>2
GROUP BY category_id;
```

**Output:**


<img width="1232" height="418" alt="Screenshot 2025-11-11 001357" src="https://github.com/user-attachments/assets/1df63bbb-fcfb-4950-b9b2-8c77f1c3e690" />


**Question 9**
---

<img width="1203" height="481" alt="Screenshot 2025-11-11 001431" src="https://github.com/user-attachments/assets/b5d13c0e-384d-4784-b382-3ccd92b49142" />


```
SELECT (CAST(age/5 AS INTEGER)*5) AS age_group,
      SUM(CAST(salary AS INTEGER)) 
FROM customer1
GROUP BY CAST(age/5 AS INTEGER)*5
HAVING SUM(CAST(salary AS INTEGER)>5000
ORDER BY age_group;
```

**Output:**


<img width="1212" height="634" alt="Screenshot 2025-11-11 001501" src="https://github.com/user-attachments/assets/e0af36ff-8d79-4c84-916c-be17265692ad" />


**Question 10**
---

<img width="1130" height="475" alt="Screenshot 2025-11-11 001531" src="https://github.com/user-attachments/assets/6786e83b-1a01-4c56-89a9-5e55c4bbd6f0" />


```
SELECT COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```

**Output:**


<img width="1199" height="389" alt="Screenshot 2025-11-11 001606" src="https://github.com/user-attachments/assets/7e81a644-244c-47b6-9f04-df784e5d6452" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
