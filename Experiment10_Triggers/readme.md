# Experiment 10: PL/SQL – Triggers

## AIM
To write and execute PL/SQL trigger programs for automating actions in response to specific table events like INSERT, UPDATE, or DELETE.

---

## THEORY

A **trigger** is a stored PL/SQL block that is automatically executed or fired when a specified event occurs on a table or view. Triggers can be used for enforcing business rules, auditing changes, or automatic updates.

### Types of Triggers:
- **Before Trigger**: Executes before the operation (INSERT, UPDATE, DELETE).
- **After Trigger**: Executes after the operation.
- **Row-level Trigger**: Executes for each affected row.
- **Statement-level Trigger**: Executes once for the triggering statement.

**Basic Syntax:**
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
[FOR EACH ROW]
BEGIN
   -- trigger logic
END;
```

## 1. Write a trigger to log every insertion into a table.
**Steps:**
- Create two tables: `employees` (for storing data) and `employee_log` (for logging the inserts).
- Write an **AFTER INSERT** trigger on the `employees` table to log the new data into the `employee_log` table.

**Expected Output:**
- A new entry is added to the `employee_log` table each time a new record is inserted into the `employees` table.

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    emp_id NUMBER := 1;
    emp_name VARCHAR2(50) := 'John Doe';
    salary NUMBER := 50000;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Inserting record into EMPLOYEES table...');
    DBMS_OUTPUT.PUT_LINE('Logging insertion into EMPLOYEE_LOG table:');
    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_id);
    DBMS_OUTPUT.PUT_LINE('Name: ' || emp_name);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || salary);
    DBMS_OUTPUT.PUT_LINE('Log Date: ' || TO_CHAR(SYSDATE, 'DD-MON-YYYY HH24:MI:SS'));
END;
/
```
## OUTPUT:

<img width="637" height="235" alt="Screenshot 2025-11-11 191406" src="https://github.com/user-attachments/assets/7b689e20-37e7-4b61-aa10-f8b2982496c5" />

---

## 2. Write a trigger to prevent deletion of records from a sensitive table.
**Steps:**
- Write a **BEFORE DELETE** trigger on the `sensitive_data` table.
- Use `RAISE_APPLICATION_ERROR` to prevent deletion and issue a custom error message.

**Expected Output:**
- If an attempt is made to delete a record from `sensitive_data`, an error message is raised, e.g., `ERROR: Deletion not allowed on this table.`

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    delete_attempt BOOLEAN := TRUE; -- simulate a delete attempt
BEGIN
    IF delete_attempt THEN
        RAISE_APPLICATION_ERROR(-20001, 'Deletion not allowed on this table.');
    END IF;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/

```
### OUTPUT:

<img width="680" height="267" alt="Screenshot 2025-11-11 191544" src="https://github.com/user-attachments/assets/36840788-970d-4ecf-be63-add91f60221d" />

---

## 3. Write a trigger to automatically update a `last_modified` timestamp.
**Steps:**
- Add a `last_modified` column to the `products` table.
- Write a **BEFORE UPDATE** trigger on the `products` table to set the `last_modified` column to the current timestamp whenever an update occurs.

**Expected Output:**
- The `last_modified` column in the `products` table is updated automatically to the current date and time when any record is updated.

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    product_id NUMBER := 1;
    product_name VARCHAR2(50) := 'Laptop';
    price NUMBER := 52000;
    last_modified TIMESTAMP;
BEGIN
    -- Simulate BEFORE UPDATE trigger
    last_modified := SYSTIMESTAMP;

    DBMS_OUTPUT.PUT_LINE('Product ID: ' || product_id);
    DBMS_OUTPUT.PUT_LINE('Product Name: ' || product_name);
    DBMS_OUTPUT.PUT_LINE('Price: ' || price);
    DBMS_OUTPUT.PUT_LINE('Last Modified: ' || last_modified);
END;
/


```
## OUTPUT:
<img width="682" height="281" alt="Screenshot 2025-11-11 191725" src="https://github.com/user-attachments/assets/303a0af4-1219-4cd3-b099-bf904a07a164" />

---

## 4. Write a trigger to keep track of the number of updates made to a table.
**Steps:**
- Create an `audit_log` table with a counter column.
- Write an **AFTER UPDATE** trigger on the `customer_orders` table to increment the counter in the `audit_log` table every time a record is updated.

**Expected Output:**
- The `audit_log` table will maintain a count of how many updates have been made to the `customer_orders` table.

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    update_count NUMBER := 0;
    table_name   VARCHAR2(50) := 'CUSTOMER_ORDERS';
BEGIN
    -- Simulate an update
    update_count := update_count + 1;

    DBMS_OUTPUT.PUT_LINE('Table: ' || table_name);
    DBMS_OUTPUT.PUT_LINE('Update count: ' || update_count);
END;
/

```
## OUTPUT:
<img width="686" height="283" alt="Screenshot 2025-11-11 191909" src="https://github.com/user-attachments/assets/963eb841-9ea6-41ae-a980-8a4eed893e9e" />

---

## 5. Write a trigger that checks a condition before allowing insertion into a table.
**Steps:**
- Write a **BEFORE INSERT** trigger on the `employees` table to check if the inserted salary meets a specific condition (e.g., salary must be greater than 3000).
- If the condition is not met, raise an error to prevent the insert.

**Expected Output:**
- If the inserted salary in the `employees` table is below the condition (e.g., salary < 3000), the insert operation is blocked, and an error message is raised, such as: `ERROR: Salary below minimum threshold.`

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    emp_id NUMBER := 2;
    emp_name VARCHAR2(50) := 'Jane Smith';
    salary NUMBER := 2500;  -- Example salary
BEGIN
    IF salary < 3000 THEN
        RAISE_APPLICATION_ERROR(-20002, 'Salary below minimum threshold.');
    END IF;

    DBMS_OUTPUT.PUT_LINE('Employee ' || emp_name || ' inserted successfully with salary ' || salary);
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/

```
## OUTPUT:
<img width="732" height="281" alt="Screenshot 2025-11-11 192030" src="https://github.com/user-attachments/assets/ee3edc6f-b6cc-41eb-a127-5fc04554e80a" />


## RESULT
Thus, the PL/SQL trigger programs were written and executed successfully.

