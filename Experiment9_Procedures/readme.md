<img width="923" height="374" alt="image" src="https://github.com/user-attachments/assets/62559ce6-3525-45e6-98d2-d6e2c7f1f04b" /># Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 6;
    sq  NUMBER;
BEGIN
    sq := num * num;
    DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || sq);
END;
/
```

## OUTPUT: 

<img width="923" height="374" alt="Screenshot 2025-11-11 190127" src="https://github.com/user-attachments/assets/d65e307b-3c11-4cac-9451-f4a0d630c14a" />


---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 5;
    fact NUMBER := 1;
    i NUMBER;
BEGIN
    FOR i IN 1..num LOOP
        fact := fact * i;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is ' || fact);
END;
/
```
## OUTPUT:
<img width="799" height="287" alt="Screenshot 2025-11-11 190427" src="https://github.com/user-attachments/assets/bd4bd8e6-0f37-4441-a084-da781987e08c" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 12;  -- You can change this value
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
    END IF;
END;
/
```
## OUTPUT:

<img width="761" height="269" alt="Screenshot 2025-11-11 190642" src="https://github.com/user-attachments/assets/c0bb2f03-d081-48a4-b075-59a93f3efe6b" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 1234;   -- You can change this value
    rev NUMBER := 0;
    n   NUMBER := num;
BEGIN
    WHILE n > 0 LOOP
        rev := rev * 10 + MOD(n, 10);
        n := FLOOR(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || num || ' is ' || rev);
END;
/
```
## OUTPUT:

<img width="667" height="285" alt="Screenshot 2025-11-11 190844" src="https://github.com/user-attachments/assets/7c9a965d-73ff-4059-88f9-3f7533892462" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## PROGRAM:
```
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := 5;  -- You can change this value
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;
/
```
## OUTPUT:

<img width="691" height="294" alt="Screenshot 2025-11-11 191011" src="https://github.com/user-attachments/assets/90ff5783-30e1-4484-a4ec-d15238092393" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
