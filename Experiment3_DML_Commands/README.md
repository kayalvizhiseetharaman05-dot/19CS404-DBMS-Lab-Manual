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
```
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability
```

```
update products set availability=availability*2 where product_id=1;
```

**Output:**

<img width="1213" height="241" alt="image" src="https://github.com/user-attachments/assets/6a124911-2c28-4b9b-9c62-313fc8327436" />


**Question 2**
```
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)
```

```
update suppliers set supplier_name='A1 Suppliers' where supplier_id=8;
```

**Output:**

<img width="1210" height="426" alt="image" src="https://github.com/user-attachments/assets/c5d14978-dd3a-4664-b0da-7eba3f58be5d" />


**Question 3**
```
 Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
```
```
update SALES set total_sell_price=quantity*sell_price where product_id=10;
```

**Output:**

 <img width="1225" height="517" alt="image" src="https://github.com/user-attachments/assets/b1a92f8a-97bd-460c-b44e-bf2f766e6cb9" />


**Question 4**
<img width="1228" height="301" alt="image" src="https://github.com/user-attachments/assets/89c1ba7d-9e07-4022-beec-7e6a03b1b6b1" />


```
delete from Customer where GRADE%2 =1;
```

**Output:**

<img width="1216" height="436" alt="image" src="https://github.com/user-attachments/assets/2ae420ef-9754-4430-9e42-19f1d156173d" />


**Question 5**
```
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
```
Delete from Doctors where last_name is null;
```

**Output:**

<img width="1196" height="712" alt="image" src="https://github.com/user-attachments/assets/e3f5c917-59de-4b51-bbb1-701652f2dfc4" />


**Question 6**

<img width="1183" height="181" alt="image" src="https://github.com/user-attachments/assets/542bef91-1f08-4972-a8e0-84c7b5f711c4" />



```
select * from EmployeeInfo where EmpFname not in("Sanjay","Sonia");
```

**Output:**

<img width="1213" height="277" alt="image" src="https://github.com/user-attachments/assets/73d77c93-92ad-4439-981b-b52c840bfdb5" />


**Question 7**
<img width="917" height="297" alt="image" src="https://github.com/user-attachments/assets/b67a9253-0d2f-4e63-b854-212fddce4e14" />


```
select id,value1, case when cast(value1 as integer)%2=0 then 'Even' else 'Odd' end as parity from Calculations  ;

```

**Output:**

<img width="812" height="495" alt="image" src="https://github.com/user-attachments/assets/d7b45b89-0a95-4e33-999b-988253355a1b" />


**Question 8**
<img width="1217" height="380" alt="image" src="https://github.com/user-attachments/assets/fae4bf7f-77ea-4e5b-8aeb-978a642f903d" />


```
select * from orders where not (ord_date='2012-08-17'or(customer_id>3005 and purch_amt<1000));
```

**Output:**

<img width="1178" height="787" alt="image" src="https://github.com/user-attachments/assets/6b24eae9-312f-4412-9441-99c7fbc8aa4a" />


**Question 9**
```
Write a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage
------------+----------------+---------------------
101 | 50.00 | 0.10
102 | 75.00 | 0.15
103 | 100.00 | 0.20
```

```
select product_id,original_price,discount_percentage,original_price*(1-discount_percentage) as discounted_price from Products;
```

**Output:**

<img width="1237" height="457" alt="image" src="https://github.com/user-attachments/assets/881397c5-70d5-440a-82fb-a69f95d66c28" />


**Question 10**
```
Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.
```
```
select substr(hiredate,1,4) as Year,
substr(hiredate,6,2) as Month ,
substr (hiredate,9,2) as Day from emp;
```

**Output:**

<img width="837" height="367" alt="image" src="https://github.com/user-attachments/assets/5d8e762f-38ca-4077-9216-e5bb115b44d3" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
