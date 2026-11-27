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

Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
For example:

Test	Result
select changes();
changes()
-----------------
4

```sql
UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="991" height="431" alt="image" src="https://github.com/user-attachments/assets/4c79204f-7885-4341-84cf-a31375c40abb" />


**Question 2**
Write a SQL query to select orders between 500 and 4000 (begin and end values are included). Exclude orders amount 948.50 and 1983.43. Return ord_no, purch_amt, ord_date, customer_id, and salesman_id.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
For example:

Result
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70003       2480.4      2012-10-10  3009         5003
70013       3045.6      2012-04-25  3002         5001

```sql
SELECT * FROM orders
WHERE (purch_amt NOT IN (948.50, 1983.43) AND (purch_amt BETWEEN 500 AND 4000));
```

**Output:**
<img width="1012" height="427" alt="image" src="https://github.com/user-attachments/assets/6f7c1af3-b876-497e-aade-695d67a0e4d9" />


**Question 3**
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT
For example:

Test	Result
select changes();
changes()
----------
4


```sql
UPDATE products
SET sell_price = sell_price * 1.15
WHERE (quantity < 50 AND supplier_id = 10);
```

**Output:**

<img width="1003" height="530" alt="image" src="https://github.com/user-attachments/assets/d5f1532f-af13-49ca-9cf6-c9134e93edd6" />


**Question 4**
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics


```sql
DELETE FROM Doctors
where (specialization IN ('Pediatrics', 'Cardiology') AND last_name = 'Brown');
```

**Output:**

<img width="1006" height="781" alt="image" src="https://github.com/user-attachments/assets/e6c6a472-9657-4806-a9a6-011bafd4874e" />


**Question 5**
Write a query to find the top 2 products with the highest discount percentage. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage
-----------------------------------------------------------
"101" "50" "0.1"
"102" "150" "0.15"
"103" "200" "0.2"
"104" "300" "0.25"
For example:

Result
product_id  original_price  discount_percentage  discounted_price
----------  --------------  -------------------  ----------------
104         300.0           0.25                 225.0
103         200.0           0.2                  160.0

```sql
SELECT product_id, original_price, discount_percentage, (original_price * (1 - discount_percentage)) AS discounted_price
FROM Products
ORDER BY discounted_price DESC LIMIT 2;
```

**Output:**

<img width="998" height="232" alt="image" src="https://github.com/user-attachments/assets/70b5478d-9aab-4bc3-997d-d5355a3be584" />


