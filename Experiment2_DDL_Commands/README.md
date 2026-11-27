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
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

For example:

Test Result SELECT * FROM Customers WHERE CustomerID = 301; CustomerID Name Address City ZipCode

301 Michael Jordan 123 Maple St Chicago 60616

```sql
INSERT INTO Customers (CustomerID, Name, Address, City, Zipcode)
VALUES (301, 'Michael Jordan', '123 Maple St', 'Chicago', 60616);
```

**Output:**
<img width="1003" height="266" alt="image" src="https://github.com/user-attachments/assets/81607bd7-220a-49ed-9321-a3483a6ec327" />


**Question 2**
Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

cid name type notnull dflt_value pk

0 RollNo int 0 1 1 Name VARCH 1 0 2 Gender TEXT 1 0 3 Subject VARCH 0 0 4 MARKS INT ( 0 0 For example:

Test Result pragma table_info('Student_details'); cid name type notnull dflt_value pk

0 RollNo int 0 1 1 Name VARCHAR(10 1 0 2 Gender TEXT 1 0 3 Subject VARCHAR(30 0 0 4 MARKS INT (3) 0 0 5 State TEXT 0 0

```sql
-- ALTER TABLE Student_details
ADD COLUMN State TEXT;
```

**Output:**

<img width="1003" height="342" alt="image" src="https://github.com/user-attachments/assets/6bb1b332-3654-4fa3-ae65-b3c6e2951664" />


**Question 3**
Create a table named Shipments with the following constraints: ShipmentID as INTEGER should be the primary key. ShipmentDate as DATE. SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID). OrderID as INTEGER should be a foreign key referencing Orders(OrderID). For example:

Test Result INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1); Error: FOREIGN KEY constraint failed

```sql
-- CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER REFERENCES Suppliers(SupplierID),
    OrderID INTEGER REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1002" height="255" alt="image" src="https://github.com/user-attachments/assets/7fcb3a8c-110f-40ed-8166-68059f31e640" />


**Question 4**
Create a new table named orders with the following specifications: ord_id as TEXT with a length of 4. item_id as TEXT. ord_date as DATE. ord_qty as INTEGER. cost as INTEGER. The primary key is a composite key consisting of item_id and ord_date. ord_id and item_id should not accept NULL For example:

Test Result INSERT INTO orders (ord_id, item_id, ord_date, ord_qty, cost) VALUES ('O001', 'I001', '2023-08-01', 10, 100); SELECT * FROM orders; ord_id item_id ord_date ord_qty cost

```sql
-- CREATE TABLE orders (
    ord_id TEXT NOT NULL CHECK (LENGTH(ord_id) = 4),
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGERS,
    cost INTEGER,
    PRIMARY KEY (item_id, ord_date)
);
```

**Output:**
<img width="981" height="332" alt="image" src="https://github.com/user-attachments/assets/528e7f12-1273-4c9a-a924-a707aaaf6f76" />


**Question 5**
Question 5 ---In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo Name Gender Subject MARKS

205 Olivia Green F 207 Liam Smith M Mathematics 85 208 Sophia Johnson F Science For example:

Test Result select * from Student_details; RollNo Name Gender Subject MARKS

205 Olivia Green F 207 Liam Smith M Mathematic 85 208 Sophia Johns F Science

```sql
-- INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (205, 'Olivia Green', 'F', NULL, NULL);
INSERT INTO Student_details (RollNO, Name, Gender, Subject, MARKS)
VALUES (207, 'Liam Smith', 'M', 'Mathematic', 85);
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (208, 'Sophia Johnson', 'F', 'Science', NULL);
```

**Output:**
<img width="1000" height="290" alt="image" src="https://github.com/user-attachments/assets/fdfd32e1-e68c-43de-8707-cf038fc6693f" />


 of constraints and DDL commands have been executed successfully.
