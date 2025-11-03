# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1384" height="468" alt="Screenshot 2025-11-03 161119" src="https://github.com/user-attachments/assets/1f49e184-bd37-428f-ae52-f299e64e5a74" />


```
CREATE TABLE Customers(
     CustomerID INTEGER,
     Name TEXT,
     Email TEXT,
     JoinDate DATETIME
);
```

**Output:**

<img width="1232" height="488" alt="Screenshot 2025-11-03 161155" src="https://github.com/user-attachments/assets/aacba99a-d002-4b86-ba7d-d8632b0124a4" />


**Question 2**
---
<img width="1408" height="447" alt="Screenshot 2025-11-03 161215" src="https://github.com/user-attachments/assets/63db55dd-9abe-4809-a06e-04ebe5ae3dc9" />


```
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE,
    Salary DECIMAL(10,2) CHECK(Salary>0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**
<img width="1228" height="505" alt="Screenshot 2025-11-03 161253" src="https://github.com/user-attachments/assets/11fab163-6218-4160-8a16-8ad2d18a4711" />


**Question 3**
---
<img width="1407" height="313" alt="Screenshot 2025-11-03 161313" src="https://github.com/user-attachments/assets/b92cd50e-332b-49a4-8b22-f191587a2bf0" />


```
CREATE TABLE jobs(
    job_id INT PRIMARY KEY,
    job_title VARCHAR(50),
    min_salary INT DEFAULT 8000,
    max_salary INT DEFAULT NULL
);
```

**Output:**

<img width="1232" height="413" alt="Screenshot 2025-11-03 161355" src="https://github.com/user-attachments/assets/5c1b58fb-6e49-452a-92b7-010b34ca7938" />


**Question 4**
---
<img width="1408" height="367" alt="Screenshot 2025-11-03 161416" src="https://github.com/user-attachments/assets/fe2810ac-bd97-4b1d-811e-d69d1a9c83c4" />


```
ALTER TABLE employee
ADD COLUMN first_name varchar(50);
ALTER TABLE employee
ADD COLUMN last_name varchar(50);
```

**Output:**

<img width="1245" height="399" alt="Screenshot 2025-11-03 161447" src="https://github.com/user-attachments/assets/533ac748-0486-44c6-a94a-d381319547b1" />


**Question 5**
---
<img width="1411" height="513" alt="Screenshot 2025-11-03 161505" src="https://github.com/user-attachments/assets/644c86b3-72a5-446c-b988-c0cf31a3bd64" />


```
ALTER TABLE employee
ADD COLUMN department_id INTEGER;
ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1227" height="395" alt="Screenshot 2025-11-03 161539" src="https://github.com/user-attachments/assets/6d46f08a-3f95-4524-9b37-7fde8689dede" />


**Question 6**
---
<img width="1405" height="367" alt="Screenshot 2025-11-03 161603" src="https://github.com/user-attachments/assets/dc214399-1227-48c1-9d19-6982738c5b0b" />


```
INSERT INTO Products(ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM  Discontinued_products;
```

**Output:**

<img width="1236" height="379" alt="Screenshot 2025-11-03 161643" src="https://github.com/user-attachments/assets/225df2db-8fe3-4cd6-a3f5-8da067c00950" />


**Question 7**
---
<img width="1408" height="506" alt="Screenshot 2025-11-03 161702" src="https://github.com/user-attachments/assets/fc1f65ed-b3df-418b-b2fc-8caa5b291233" />


```
INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode)
VALUES(306,'Diana Prince','Themyscira',NULL,NULL);
INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode)
VALUES(307,'Bruce Wayne','Wayne Mano','Gotham','10007');
INSERT INTO Customers(CustomerID, Name, Address, City, ZipCode)
VALUES(308,'Peter Parker','Queens',NULL,'11375');

```

**Output:**

<img width="1231" height="359" alt="Screenshot 2025-11-03 161808" src="https://github.com/user-attachments/assets/5b5a23fb-f0f1-4abe-900d-52da0cd6e0cf" />


**Question 8**
---
<img width="1401" height="435" alt="Screenshot 2025-11-03 161828" src="https://github.com/user-attachments/assets/e5bf0f49-859c-464f-bdd3-ad70ee53c6d5" />


```
INSERT INTO Customers(CustomerID, Name,Address)
VALUES(304,'Peter Parker','Spider St')
SELECT CustomerID,Name,Address,City,ZipCode FROM Customers;

```

**Output:**

<img width="1243" height="743" alt="Screenshot 2025-11-03 161901" src="https://github.com/user-attachments/assets/47ed228f-2cfd-4b1a-adb8-0614a62d1062" />

**Question 9**
---
<img width="1402" height="416" alt="Screenshot 2025-11-03 161922" src="https://github.com/user-attachments/assets/70da7cea-ae85-42cd-83ab-0e101cacbbe2" />


```
CREATE TABLE Products(
     ProductID INTEGER PRIMARY KEY,
     ProductName TEXT UNIQUE NOT NULL,
     Price REAL NOT NULL CHECK(Price>0),
     StockQuantity INTEGER NOT NULL CHECK(StockQuantity >=0) 
);
```

**Output:**

<img width="1230" height="368" alt="Screenshot 2025-11-03 161956" src="https://github.com/user-attachments/assets/9a28dfb3-12c9-4d3b-b8b9-64b00d3cff6c" />


**Question 10**
---

<img width="1407" height="464" alt="Screenshot 2025-11-03 162017" src="https://github.com/user-attachments/assets/33d3219b-941f-4e8b-b6cf-9a26d82bbe84" />


```
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**


<img width="1235" height="438" alt="Screenshot 2025-11-03 162104" src="https://github.com/user-attachments/assets/01c65e36-298b-46cb-9bca-8ef84d51c57f" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
