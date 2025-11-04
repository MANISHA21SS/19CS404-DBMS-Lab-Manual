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
--
<img width="1373" height="563" alt="Screenshot 2025-11-04 155818" src="https://github.com/user-attachments/assets/4645bf35-b371-444e-ba69-b94b2696d532" />


```
UPDATE products
SET sell_price = sell_price * 1.15
WHERE quantity < 50 AND supplier_id = 10;

```

**Output:**

<img width="1239" height="568" alt="Screenshot 2025-11-04 155908" src="https://github.com/user-attachments/assets/4c8ee78a-49e5-49df-8ece-de7535a56199" />


**Question 2**
---
<img width="1381" height="601" alt="Screenshot 2025-11-04 155938" src="https://github.com/user-attachments/assets/37d06b30-8d60-4c41-a7e5-e42277cd23eb" />


```
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE cost_price > 50 AND quantity < 100;

```

**Output:**

<img width="1226" height="536" alt="Screenshot 2025-11-04 160013" src="https://github.com/user-attachments/assets/9a785a28-e108-4fbc-8094-931b2abafbff" />


**Question 3**
---
<img width="1391" height="509" alt="Screenshot 2025-11-04 160037" src="https://github.com/user-attachments/assets/cb4e60e9-e492-4150-ad30-333911ff399e" />


```
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10 AND category = 'Snacks';

```

**Output:**

<img width="1236" height="663" alt="Screenshot 2025-11-04 160115" src="https://github.com/user-attachments/assets/b4dda1f2-ecb3-42d3-9cdd-c80829044ad3" />


**Question 4**
---
<img width="1408" height="613" alt="Screenshot 2025-11-04 160138" src="https://github.com/user-attachments/assets/cebaab02-4019-440a-8755-fe26db0539b2" />


```
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE product_name LIKE '%cream%'
  AND quantity > reorder_lvl;

```

**Output:**

<img width="1238" height="574" alt="Screenshot 2025-11-04 160213" src="https://github.com/user-attachments/assets/4b364b14-35b9-4850-af65-600842f566c5" />


**Question 5**
---
<img width="1400" height="296" alt="Screenshot 2025-11-04 160233" src="https://github.com/user-attachments/assets/d0327693-bfbb-40a6-b8bd-a4f7ecad00cd" />


```
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';

```

**Output:**

<img width="1305" height="531" alt="Screenshot 2025-11-04 160307" src="https://github.com/user-attachments/assets/5a27219c-b72b-47d7-9a63-18a6c0c3929c" />


**Question 6**
---
<img width="1398" height="187" alt="Screenshot 2025-11-04 160330" src="https://github.com/user-attachments/assets/82c7cc4e-3002-4d49-894c-83aadc48a38c" />


```
DELETE FROM Doctors
WHERE specialization = 'Pediatrics' AND first_name = 'Michael';

```

**Output:**

<img width="1234" height="455" alt="Screenshot 2025-11-04 160402" src="https://github.com/user-attachments/assets/06031d1a-62f8-4fa8-a7de-9d13adeed0e0" />


**Question 7**
---
<img width="1404" height="165" alt="Screenshot 2025-11-04 160427" src="https://github.com/user-attachments/assets/7c512fb0-1907-4e12-8094-dd20ab9410e4" />


```
DELETE FROM Doctors
WHERE specialization = 'Cardiology';

```

**Output:**

<img width="1232" height="460" alt="Screenshot 2025-11-04 160501" src="https://github.com/user-attachments/assets/3f9bc008-5135-4af4-9817-ae7f7b0fc7b3" />


**Question 8**
---
<img width="1407" height="518" alt="Screenshot 2025-11-04 160525" src="https://github.com/user-attachments/assets/89919955-08da-4afc-9ab8-b217a721df09" />


```
DELETE FROM Customer
WHERE (grade > 2 AND payment_amt < (SELECT AVG(payment_amt) FROM Customer))
   OR outstanding_amt > 8000;

```

**Output:**

<img width="1237" height="753" alt="Screenshot 2025-11-04 160556" src="https://github.com/user-attachments/assets/0383bd7e-fb36-4490-ac3f-142c8e49976b" />


**Question 9**
---
<img width="1414" height="490" alt="Screenshot 2025-11-04 160618" src="https://github.com/user-attachments/assets/81424b67-e009-4a27-9f91-53b141a15de5" />


```
DELETE FROM Customer
WHERE cust_country = 'UK' AND working_area = 'London' AND grade < 3;

```

**Output:**

<img width="1226" height="549" alt="Screenshot 2025-11-04 160706" src="https://github.com/user-attachments/assets/cdfbf790-52e8-4d6d-aebd-b51b0d477e10" />


**Question 10**
---
<img width="1405" height="666" alt="Screenshot 2025-11-04 160731" src="https://github.com/user-attachments/assets/5058cc1c-942a-44fb-ba3a-8d6e16766375" />


```
DELETE FROM Surgeries
WHERE surgery_id = 3 OR surgeon_id = 4;

```

**Output:**

<img width="1223" height="832" alt="Screenshot 2025-11-04 160806" src="https://github.com/user-attachments/assets/616ef6f0-a7f2-43ca-9f9a-6fcd5f239dce" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
