<img width="832" height="269" alt="image" src="https://github.com/user-attachments/assets/4058538c-2d22-4ffa-a1b6-559c44a25de2" /># Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80
## PROGRAM:
```
DECLARE
    num1 NUMBER := 50;
    num2 NUMBER := 80;
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
/


```
### OUTPUT:

<img width="832" height="269" alt="Screenshot 2025-11-03 160048" src="https://github.com/user-attachments/assets/fedc6993-c432-4e19-981e-523b1320fdfe" />



## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

## PROGRAM:
```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```
### OUTPUT:

<img width="987" height="360" alt="Screenshot 2025-11-03 160235" src="https://github.com/user-attachments/assets/8447cf4b-c29c-4f97-9603-e3b332b0d712" />


## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8


## PROGRAM:
```
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    
    WHILE i <= n LOOP
        IF i = 1 THEN
            DBMS_OUTPUT.PUT_LINE(a);
        ELSIF i = 2 THEN
            DBMS_OUTPUT.PUT_LINE(b);
        ELSE
            c := a + b;
            DBMS_OUTPUT.PUT_LINE(c);
            a := b;
            b := c;
        END IF;
        i := i + 1;
    END LOOP;
END;
/
```
## OUTPUT:

<img width="989" height="360" alt="Screenshot 2025-11-03 160352" src="https://github.com/user-attachments/assets/6bca82cc-5511-46eb-93c3-7b553b8da68e" />


## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

## PROGRAM:
```
DECLARE
    n NUMBER := 1535;
    temp NUMBER;
    rev NUMBER := 0;
BEGIN
    temp := n;  -- Store original number
    
    WHILE temp > 0 LOOP
        rev := (rev * 10) + MOD(temp, 10);
        temp := FLOOR(temp / 10);
    END LOOP;
    
    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```
## OUTPUT:

<img width="914" height="365" alt="Screenshot 2025-11-03 160503" src="https://github.com/user-attachments/assets/73ad3db5-455e-4caf-8881-845651c4c847" />


## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## PROGRAM:
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```

## OUTPUT:

<img width="871" height="360" alt="Screenshot 2025-11-03 160601" src="https://github.com/user-attachments/assets/84d55ea5-d433-46db-99e9-df4d7a4eb394" />



## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

