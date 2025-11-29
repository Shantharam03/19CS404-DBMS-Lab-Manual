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
<img width="802" height="449" alt="image" src="https://github.com/user-attachments/assets/d27c3580-cb12-458b-ac65-7840309fc96e" />


```sql
ALTER TABLE Student_details
ADD COLUMN Mobilenumber number;
```

**Output:**
<img width="1139" height="207" alt="image" src="https://github.com/user-attachments/assets/305dbff2-9303-4e0b-95ef-70b041b5896e" />



**Question 2**
---
<img width="726" height="349" alt="image" src="https://github.com/user-attachments/assets/1ff3bd7f-3fb9-48bd-a993-ad570782d80a" />


```sql
create table Employees(
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1136" height="165" alt="image" src="https://github.com/user-attachments/assets/18ee0967-0f9d-498c-ad20-0d086cbaf947" />

**Question 3**
---
<img width="607" height="263" alt="image" src="https://github.com/user-attachments/assets/0d6a4d3b-c101-4062-8131-9a9a14027fd9" />


```sql
insert into Employee select * from Former_employees
```

**Output:**

<img width="895" height="157" alt="image" src="https://github.com/user-attachments/assets/e7ae1b2d-a5bf-4c9b-994b-aa60b42e13ca" />


**Question 4**
---
<img width="841" height="447" alt="image" src="https://github.com/user-attachments/assets/39b4bea5-3aa5-48ad-abb3-8a5ad0f5088d" />


```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
alter table Companies add column dob date;
```

**Output:**

<img width="1133" height="219" alt="image" src="https://github.com/user-attachments/assets/b89b0b6f-744f-483d-9e07-f1ce95225a0e" />


**Question 5**
---
<img width="763" height="268" alt="image" src="https://github.com/user-attachments/assets/a00b42bb-32f3-4040-bf34-806d790f89f7" />

```sql
create table Invoices(
    InvoiceID integer primary key,
    InvoiceDate date,
    DueDate date check (DueDate > InvoiceDate),
    Amount real check (Amount > 0)
);
```

**Output:**

<img width="1113" height="149" alt="image" src="https://github.com/user-attachments/assets/8fc548b5-78b6-4a13-9859-cc8e3791a8ef" />

**Question 6**
---
<img width="1136" height="284" alt="image" src="https://github.com/user-attachments/assets/88053f65-a023-4414-b9c5-ab1091c1acea" />

```sql
insert into Student_details (RollNo, Name, Gender, Subject, MARKS) VALUES (205,'Olivia Green','F','','');
insert into Student_details (RollNo, Name, Gender, Subject, MARKS) VALUES (207,'Liam Smith','M','Mathematic',85);
insert into Student_details (RollNo, Name, Gender, Subject, MARKS) VALUES (208,'Sophia Johns','F','Science','');
```

**Output:**

<img width="1141" height="152" alt="image" src="https://github.com/user-attachments/assets/229c7740-ebda-44a8-9887-6998ed7a168b" />

**Question 7**
---
<img width="1128" height="331" alt="image" src="https://github.com/user-attachments/assets/60c67312-1142-4de9-9eca-38f3c570dec0" />

```sql
create table orders(
    ord_id not null,
    item_id text not null,
    ord_date date,
    ord_qty integer,
    cost integer,
    primary key (item_id,ord_date),
    check (length(ord_id) = 4)
);
```

**Output:**

<img width="1137" height="123" alt="image" src="https://github.com/user-attachments/assets/342ed93d-360b-4e06-b32b-44e702e46f19" />

**Question 8**
---
<img width="939" height="188" alt="image" src="https://github.com/user-attachments/assets/18127d49-ec87-4a26-97e0-51a58df52f38" />

```sql
insert into Employee values (1,'Sarah Parker', 'Manager', 'HR', 60000)
```

**Output:**

<img width="1134" height="142" alt="image" src="https://github.com/user-attachments/assets/ea5cda28-c5ca-424f-8e6d-74bb3984652b" />

**Question 9**
---
<img width="1066" height="317" alt="image" src="https://github.com/user-attachments/assets/65a06ddb-1bfe-45b3-870e-911d09a6ec75" />

```sql
create table Employees(
    EmployeeID integer primary key,
    FirstName text not null,
    LastName text not null,
    Email varchar unique,
    Salary integer,
    DepartmentID integer,
    foreign key (DepartmentID) references Departments(DepartmentID),
    check (Salary > 0)
);
```

**Output:**

<img width="1120" height="225" alt="image" src="https://github.com/user-attachments/assets/1879ff90-7c80-45e0-b1ba-23ad0270a27c" />

**Question 10**
---
<img width="862" height="392" alt="image" src="https://github.com/user-attachments/assets/c9834fcd-73e2-4775-b034-1f2415399631" />

```sql
INSERT INTO Student_details (RollNo, Name, Gender) values (204, 'Samuel Black', 'M');
```

**Output:**

<img width="956" height="225" alt="image" src="https://github.com/user-attachments/assets/145d1d20-c96b-4be9-b2db-91f1e096db53" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
