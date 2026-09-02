# Experiment 9: PL/SQL – Procedures and Functions

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

**Program:**
```
CREATE OR REPLACE PROCEDURE find_square (p_num IN NUMBER) IS
    v_square NUMBER;
BEGIN
    v_square := p_num * p_num;
    DBMS_OUTPUT.PUT_LINE('Square of ' || p_num || ' is ' || v_square);
END;
/

BEGIN
    find_square(6);
END;
/
```

**Result:**

<img width="568" height="257" alt="image" src="https://github.com/user-attachments/assets/2850bcc7-021a-47d9-861c-a24b5ebefaf8" />

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

**Program:**
```
CREATE OR REPLACE FUNCTION get_factorial (p_num IN NUMBER) RETURN NUMBER IS
    v_fact NUMBER := 1;
BEGIN
    FOR i IN 1..p_num LOOP
        v_fact := v_fact * i;
    END LOOP;
    RETURN v_fact;
END;
/

DECLARE
    v_num NUMBER := 5;
    v_result NUMBER;
BEGIN
    v_result := get_factorial(v_num);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || v_num || ' is ' || v_result);
END;
/
```

**Result:**

<img width="711" height="393" alt="image" src="https://github.com/user-attachments/assets/c2366f8d-2f12-41c2-8851-5b902f96e29a" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

**Program:**
```
CREATE OR REPLACE PROCEDURE check_even_odd (p_num IN NUMBER) IS
BEGIN
    IF MOD(p_num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(12);
END;
/
```

**Result:**

<img width="621" height="360" alt="image" src="https://github.com/user-attachments/assets/0ea26305-9679-43c3-b450-bc3d796044cf" />


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

**Program:**
```
CREATE OR REPLACE FUNCTION reverse_number (p_num IN NUMBER) RETURN NUMBER IS
    v_temp NUMBER := p_num;
    v_rev NUMBER := 0;
    v_rem NUMBER;
BEGIN
    WHILE v_temp > 0 LOOP
        v_rem := MOD(v_temp, 10);
        v_rev := (v_rev * 10) + v_rem;
        v_temp := TRUNC(v_temp / 10);
    END LOOP;
    RETURN v_rev;
END;
/

DECLARE
    v_num NUMBER := 1234;
    v_result NUMBER;
BEGIN
    v_result := reverse_number(v_num);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || v_num || ' is ' || v_result);
END;
/
```

**Result:**

<img width="598" height="422" alt="image" src="https://github.com/user-attachments/assets/35b3f1ef-c1ad-465f-bc94-6319acb64077" />

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

**Program:**
```
CREATE OR REPLACE PROCEDURE print_table (p_num IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || p_num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(p_num || ' x ' || i || ' = ' || (p_num * i));
    END LOOP;
END;
/

BEGIN
    print_table(5);
END;
/
```

**Result:**

<img width="555" height="447" alt="image" src="https://github.com/user-attachments/assets/9a69d228-8ca7-457e-b9d6-8cb5ea72f66c" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
