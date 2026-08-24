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
### code:
DECLARE
    a NUMBER := 25;
    b NUMBER := 40;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || b);
    END IF;
END;
/
- 

**Expected Output:**  
<img width="357" height="277" alt="image" src="https://github.com/user-attachments/assets/984033b6-a0ea-4ff1-82fa-68456ebafde6" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.
### code:
DECLARE
    n NUMBER := 10;
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers = ' || sum);
END;
/


**Expected Output:**  
<img width="468" height="256" alt="image" src="https://github.com/user-attachments/assets/ba6cce3d-4e8a-4fba-8419-3aebcd6c2e30" />


## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.
### code:
DECLARE
    n NUMBER := 10;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci Series:');

    FOR i IN 1..n LOOP
        DBMS_OUTPUT.PUT(a || ' ');
        c := a + b;
        a := b;
        b := c;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
/

**Expected Output:**  
<img width="424" height="261" alt="image" src="https://github.com/user-attachments/assets/65a56ea2-4654-4de0-b89c-c32adbebad57" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.
###code:
DECLARE
    n NUMBER := 12345;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);
        rev := rev * 10 + digit;
        n := TRUNC(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reverse of the number is: ' || rev);
END;
/

**Expected Output:**  

<img width="463" height="257" alt="image" src="https://github.com/user-attachments/assets/2fe46d95-0c34-4d9f-a75e-b39d98bcecb5" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
### code:
DECLARE
    a NUMBER := 25;
    b NUMBER := 40;
    c NUMBER := 30;
    largest NUMBER;
BEGIN
    IF a > b AND a > c THEN
        largest := a;
    ELSIF b > a AND b > c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest number is: ' || largest);
END;
/

**Expected Output:**  
<img width="403" height="263" alt="image" src="https://github.com/user-attachments/assets/d43654d4-e0a8-4b81-9e19-b199bbb12f5e" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
