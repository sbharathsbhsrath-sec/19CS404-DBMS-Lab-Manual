# Experiment 7: PL/SQL – Variables, Control Structures and Loops

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

## program:
~~~
DECLARE 
   a number :=10;
   b number :=80;
BEGIN 
   if a>b then dbms_output.put_line('Greater Number is :'|| a);
   else dbms_output.put_line('Greater Number is :'||b);
   end if;
END;


~~~
## output:
<img width="1007" height="346" alt="image" src="https://github.com/user-attachments/assets/4accfb3d-563b-40ad-a7ab-575c64dfe0dd" />



**Expected Output:**  
Greater number is: 80

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

## Program
```
SET SERVEROUTPUT ON;

DECLARE 
   n NUMBER := 5;
   v_sum NUMBER := 0; 
BEGIN 
    WHILE n > 0 LOOP
        v_sum := v_sum + n;
        n := n - 1;
    END LOOP;
    
   
    DBMS_OUTPUT.PUT_LINE('Sum: ' || v_sum);
END;
/

```
## output:
<img width="1021" height="243" alt="image" src="https://github.com/user-attachments/assets/19f2ae60-17fb-4225-905c-881ffb772dd3" />

**Expected Output:**  
Sum of first 10 natural numbers is: 55

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

## program:
```
SET SERVEROUTPUT ON;

DECLARE
   n      NUMBER := 7;
   a      NUMBER := 0;
   b      NUMBER := 1;
   c      NUMBER;
   output_str VARCHAR2(100);
BEGIN
   output_str := TO_CHAR(a);
   
   FOR i IN 2..n LOOP
      output_str := output_str || ', ' || b;
      c := a + b;
      a := b;
      b := c;
   END LOOP;
   
   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || output_str);
END;
/

```
## output
<img width="1073" height="171" alt="image" src="https://github.com/user-attachments/assets/d654f4ff-de5f-475f-84ce-9e0e293e8283" />

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

## Program:
```
SET SERVEROUTPUT ON;

DECLARE
   n         NUMBER := 1535;
   temp      NUMBER;
   reversed  NUMBER := 0;
   remainder NUMBER;
BEGIN
   temp := n;
   
   WHILE temp > 0 LOOP
      remainder := MOD(temp, 10);
      reversed := (reversed * 10) + remainder;
      temp := TRUNC(temp / 10);
   END LOOP;
   
   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
/

```
## output:
<img width="1062" height="167" alt="image" src="https://github.com/user-attachments/assets/d3195051-9ce8-4d16-b614-af054be65538" />

**Expected Output:**  
n = 1535  
Reversed number is 5351

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

## program
```
SET SERVEROUTPUT ON;

DECLARE
   a NUMBER := 45;
   b NUMBER := 82;
   c NUMBER := 37;
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
   DBMS_OUTPUT.PUT_LINE('Largest number is ' || largest);
END;
/

```
<img width="1062" height="167" alt="image" src="https://github.com/user-attachments/assets/edcefc84-6061-4277-bf69-f5293ddfd16a" />

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
