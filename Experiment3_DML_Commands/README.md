Experiment 3: DML Commands

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
--
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.
```sql
update employees
set first_name = 'John'
where department_id = 80
and commission_pct<0.35;
```

**Output:**

<img width="1136" height="507" alt="image" src="https://github.com/user-attachments/assets/bec262c8-741c-4be7-810d-713843ef05df" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'



```sql
update employees
set salary= salary * 2
where department_id = 20
and job_id LIKE '%MAN';
```

**Output:**

<img width="1134" height="345" alt="image" src="https://github.com/user-attachments/assets/51d15146-7409-4f69-96e6-214ad7729b63" />


**Question 3**
---
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.

Employees table

```sql
update employees
set salary=
case
    when department_id=40 then salary *1.25
    when department_id=90 then salary *1.15
    when department_id=110 then salary *1.10
    else salary
end    
```

**Output:**

<img width="1116" height="275" alt="image" src="https://github.com/user-attachments/assets/c95d2b5e-e8e6-4fb4-8009-73929f1cec55" />


**Question 4**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.
```sql
update purchases
set per_unit_price=25,
total_price=quantity*25
where purchase_date='2022-08-15'
and product_id = 12;```

**Output:**

![Output4](output.png)

**Question 5**
---
-- Paste Question 5 here

```sql
-- Paste your SQL code below for Question 5
```

**Output:**

<img width="1112" height="482" alt="image" src="https://github.com/user-attachments/assets/596c382e-ac95-491d-bc5c-687dc222bbf2" />

**Question 5**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

```sql
update products
set sell_price=sell_price*1.10
where category='Bakery'
```

**Output:**

<img width="1131" height="492" alt="image" src="https://github.com/user-attachments/assets/397aff51-a21e-4b23-adc5-4fb13956a0c6" />


**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000


```
delete from customer
where (GRADE=3 OR AGENT_CODE='A008')
AND OUTSTANDING_AMT<5000;
```

**Output:**

<img width="1128" height="476" alt="image" src="https://github.com/user-attachments/assets/54220418-b05d-4b60-8c55-02f622f91cd2" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.


```sql
DELETE FROM Customer
WHERE CUST_NAME LIKE'%Holmes%';
```

**Output:**

<img width="1129" height="488" alt="image" src="https://github.com/user-attachments/assets/e268bbb4-6da7-4bfa-b49e-a7a9d63149f3" />

**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.


```sql
DELETE FROM Doctors
WHERE specialization='Pediatrics'
AND First_name = 'Michael';
```

**Output:**
<img width="1123" height="478" alt="image" src="https://github.com/user-attachments/assets/be523b64-fa90-495d-b42a-b246724e5d35" />


**Question 9**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3


```sql
DELETE FROM Customer 
where CUST_COUNTRY='UK'
and WORKING_AREA= 'London'
and GRADE<3;
```

**Output:**

<img width="1125" height="485" alt="image" src="https://github.com/user-attachments/assets/31f6f85d-b386-4849-845e-c842e9775591" />

**Question 10**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000


```sql
delete from Customer
where GRADE=3
and CUST_NAME like '%BBB%'
AND PAYMENT_AMT > 2000;
```

**Output:**

<img width="1119" height="475" alt="image" src="https://github.com/user-attachments/assets/27481085-f45e-443e-be24-e2428af2a8ee" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
