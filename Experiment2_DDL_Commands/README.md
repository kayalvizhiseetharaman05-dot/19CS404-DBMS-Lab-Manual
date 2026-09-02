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
```  
   Create a table named Orders with the following columns:
   OrderID as INTEGER OrderDate as TEXT CustomerID as INTEGER
```

```
create table Orders(OrderID INTEGER,OrderDate TEXT,CustomerID INTEGER);
select * from Orders
```

**Output:**

<img width="1227" height="388" alt="image" src="https://github.com/user-attachments/assets/0542b3c4-bf10-4ac5-ac88-4d1503a65220" />


**Question 2**

 ```
Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).
```


```
alter table employee add column first_name varchar(50);
alter table employee add column last_name varchar(50); 
```

**Output:**

<img width="1182" height="306" alt="image" src="https://github.com/user-attachments/assets/14ef3dd1-32bd-4af8-a134-2c9f0fad9344" />

**Question 3**
```
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```

```
Create table Department( DepartmentID Integer Not null primary key,DepartmentName Text Not null Unique ,Location Text);
```

**Output:**

<img width="1275" height="298" alt="image" src="https://github.com/user-attachments/assets/028ef638-50f9-4a34-bacb-eac2e9778e21" />


**Question 4**
```
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```

```
Insert into Customers(CustomerID,Name,Address,City,ZipCode) values(301,'Michael Jordan','123 Maple St','Chicago','60616');
```

**Output:**

<img width="1211" height="226" alt="image" src="https://github.com/user-attachments/assets/2a5be61a-009c-4979-9549-6d27ab9efdb6" />


**Question 5**
```
Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL
```

```Create table orders(ord_id text not null 
check(length(ord_id)<=4),item_id text not null,ord_date date,ord_qty integer,cost integer,Primary key(item_id,ord_date));
```

**Output:**

<img width="1177" height="291" alt="image" src="https://github.com/user-attachments/assets/37cfc85c-f4f4-4d56-8227-a4a57634b02a" />


**Question 6**
```
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```

```
Create table Shipments(ShipmentID Integer not null Primary key,ShipmentDate Date,SupplierID Integer,OrderId Integer,Foreign key(SupplierID) references Suppliers(SupplierID),Foreign key(OrderId) references Orders(OrderID));
```

**Output:**

<img width="1228" height="255" alt="image" src="https://github.com/user-attachments/assets/231477c4-96ea-4ee1-997c-343b5248d64d" />


**Question 7**
```
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary
```

```
Insert into Employee(EmployeeID,Name,Department,Salary) select EmployeeId,Name,Department,Salary from Former_employees;
```

**Output:**

<img width="1197" height="293" alt="image" src="https://github.com/user-attachments/assets/756998ed-396b-40eb-934b-f0343498faec" />


**Question 8**
```
Write a SQL Query to Rename attribute "name" to "first_name" and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies.
```
```
alter table Companies rename column name to first_name;
alter table Companies add column mobilenumb number;
alter table Companies add column DOB Date; 
alter table Companies add column State varchar(30);
```

**Output:**

<img width="1208" height="406" alt="image" src="https://github.com/user-attachments/assets/8be417e6-73b5-4ee6-a24c-ccc77fac917b" />


**Question 9**
```
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
```
```
create table item(item_id text not null primary key,
item_desc text not null,
rate integer not null,
icom_id text check (length(icom_id)=4),
Foreign key(icom_id) references company(com_id) on update cascade on delete cascade
);
```

**Output:**

<img width="1230" height="368" alt="image" src="https://github.com/user-attachments/assets/162ceb7d-6258-46f5-b52f-d7826eae117f" />


**Question 10**
<img width="682" height="220" alt="image" src="https://github.com/user-attachments/assets/94d23c05-bd94-4eb8-86a4-f3d7db7aeb0a" />


```
Insert into Customers(ID,NAME,AGE,ADDRESS,SALARY) values (1,'Ramesh','32','Ahmedabad','2000'),
(2,'Khilan','25','Delhi','1500'),(3,'Kaushik','23','Kota','2000');
```

**Output:**

<img width="1197" height="282" alt="image" src="https://github.com/user-attachments/assets/08cdcaa4-f466-465d-911c-3b767ab2f44c" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
