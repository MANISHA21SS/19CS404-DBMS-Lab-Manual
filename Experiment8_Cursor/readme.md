# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.

**Steps:**

- Create an `employees` table with fields `emp_id`, `emp_name`, and `designation`.
- Insert some sample data into the table.
- Use a simple cursor to fetch and display employee names and designations.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Output:**  
The program should display the employee details or an error message.

## PROGRAM :
```
SET SERVEROUTPUT ON;

DECLARE
    CURSOR emp_cursor IS
        SELECT first_name || ' ' || last_name AS emp_name, job_id AS designation
        FROM hr.employees;

    v_name hr.employees.first_name%TYPE;
    v_designation hr.employees.job_id%TYPE;
    v_count NUMBER := 0;

BEGIN
    FOR rec IN emp_cursor LOOP
        v_count := v_count + 1;
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || rec.emp_name || ' | Designation: ' || rec.designation);
    END LOOP;

    IF v_count = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
## OUTPUT :
<img width="822" height="377" alt="Screenshot 2025-11-04 154044" src="https://github.com/user-attachments/assets/7b69caf7-1646-4f74-9209-5b0f0c862a2d" />

---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.

**Steps:**

- Modify the `employees` table by adding a `salary` column.
- Insert sample salary values for the employees.
- Use a parameterized cursor to accept a salary range as input and fetch employees within that range.
- Implement exception handling to catch and display relevant error messages.

**Output:**  
The program should display the employee details within the specified salary range or an error message if no data is found.

## PROGRAM :
```
SET SERVEROUTPUT ON;

DECLARE
    -- Parameterized cursor to fetch employees in a salary range
    CURSOR emp_salary_cursor(p_min_salary NUMBER, p_max_salary NUMBER) IS
        SELECT first_name || ' ' || last_name AS emp_name,
               job_id AS designation,
               salary
        FROM hr.employees
        WHERE salary BETWEEN p_min_salary AND p_max_salary;

    v_found BOOLEAN := FALSE;

BEGIN
    -- Loop through employees with salary between 5000 and 15000
    FOR emp_rec IN emp_salary_cursor(5000, 15000) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.emp_name ||
                             ', Designation: ' || emp_rec.designation ||
                             ', Salary: ' || emp_rec.salary);
    END LOOP;

    IF NOT v_found THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the given salary range.');
    END IF;

EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
## OUTPUT:
<img width="768" height="376" alt="Screenshot 2025-11-04 154530" src="https://github.com/user-attachments/assets/32fa0337-1179-43aa-a36f-426db473ad96" />


---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.

**Steps:**

- Modify the `employees` table by adding a `dept_no` column.
- Insert sample department numbers for employees.
- Use a cursor FOR loop to fetch and display employee names along with their department numbers.
- Implement exception handling to catch the relevant exceptions.

**Output:**  
The program should display employee names with their department numbers or the appropriate error message if no data is found.

## PROGRAM :
```
SET SERVEROUTPUT ON;

DECLARE
    v_found BOOLEAN := FALSE;

BEGIN
    -- Cursor FOR loop iterates automatically over each row
    FOR emp_rec IN (
        SELECT first_name || ' ' || last_name AS emp_name,
               department_id AS dept_no
        FROM hr.employees
    ) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.emp_name ||
                             ', Department No: ' || emp_rec.dept_no);
    END LOOP;

    -- Check if no rows were fetched
    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the database.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
## OUTPUT :
<img width="796" height="375" alt="Screenshot 2025-11-04 154716" src="https://github.com/user-attachments/assets/befc8f35-d8f4-4f53-b6d4-31c6cdb38f22" />


---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.

**Steps:**

- Modify the `employees` table by adding `emp_id`, `emp_name`, `designation`, and `salary` fields.
- Insert sample data into the `employees` table.
- Declare a cursor using `%ROWTYPE` to fetch complete rows from the `employees` table.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Output:**  
The program should display employee records or the appropriate error message if no data is found.

## PROGRAM :
```
SET SERVEROUTPUT ON;

DECLARE
    -- Cursor to fetch complete employee records
    CURSOR emp_cur IS
        SELECT employee_id, first_name || ' ' || last_name AS emp_name,
               job_id AS designation, salary
        FROM hr.employees;

    -- Variable to hold a row of the cursor
    emp_rec emp_cur%ROWTYPE;

    -- Flag to detect if any row is fetched
    v_found BOOLEAN := FALSE;

BEGIN
    OPEN emp_cur;

    LOOP
        FETCH emp_cur INTO emp_rec;
        EXIT WHEN emp_cur%NOTFOUND;

        v_found := TRUE;

        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_rec.employee_id ||
                             ', Name: ' || emp_rec.emp_name ||
                             ', Designation: ' || emp_rec.designation ||
                             ', Salary: ' || emp_rec.salary);
    END LOOP;

    CLOSE emp_cur;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the database.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
## OUTPUT:
<img width="837" height="388" alt="Screenshot 2025-11-04 154836" src="https://github.com/user-attachments/assets/5d52760b-3acf-4721-8f98-901763c586ec" />


---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.

**Steps:**

- Modify the `employees` table to include a `dept_no` and `salary` field.
- Insert sample data into the `employees` table with different department numbers.
- Use a cursor with the `FOR UPDATE` clause to lock the rows of employees in a specific department and update their salary.
- Implement exception handling to handle `NO_DATA_FOUND` or other errors that may occur.

**Output:**  
The program should update employee salaries and display a message, or it should display an error message if no data is found.

## PROGRAM :
```
SET SERVEROUTPUT ON;

DECLARE
    CURSOR emp_cursor IS
        SELECT employee_id, salary, department_id
        FROM hr.employees
        WHERE department_id = 60;

    v_count NUMBER := 0;

BEGIN
    FOR rec IN emp_cursor LOOP
        v_count := v_count + 1;

        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || rec.employee_id ||
                             ' | Old Salary: ' || rec.salary ||
                             ' | New Salary (after +1000): ' || (rec.salary + 1000));

        EXIT WHEN v_count = 3;
    END LOOP;

    IF v_count = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

## OUTPUT :
<img width="730" height="399" alt="Screenshot 2025-11-04 155518" src="https://github.com/user-attachments/assets/f633e66a-c308-410d-a8ed-ac6e9544b078" />


---

## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 

