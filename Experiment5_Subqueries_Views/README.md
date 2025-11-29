# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="962" height="476" alt="image" src="https://github.com/user-attachments/assets/960dac0d-d7b3-4494-8353-ce0c5d254ad5" />

```sql
--
select medication_id,medication_name,dosage from Medications
where dosage=(
     select min(dosage) from Medications);
```

**Output:**

<img width="845" height="388" alt="image" src="https://github.com/user-attachments/assets/6474f0ff-7c8d-4bc6-86e4-77871c4d347d" />

**Question 2**
---
<img width="972" height="653" alt="image" src="https://github.com/user-attachments/assets/46bfb842-0754-4f1b-86e1-d0fb25984c23" />

```sql
--
select * from CUSTOMERS
where SALARY>4500;
```

**Output:**

<img width="1108" height="370" alt="image" src="https://github.com/user-attachments/assets/64ba92a1-043e-41df-80d2-843758ee878b" />

**Question 3**
---
<img width="1134" height="629" alt="image" src="https://github.com/user-attachments/assets/d6ec8fa0-79a2-48c1-90f5-56839bc0563e" />

```sql
--
SELECT orders.ord_no,orders.purch_amt, orders.ord_date, orders.customer_id, orders.salesman_id
FROM orders 
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id
WHERE 
    salesman.city = 'New York';

```

**Output:**

<img width="1129" height="392" alt="image" src="https://github.com/user-attachments/assets/a594029c-8ead-49b1-ae1e-acf7340b7f7b" />

**Question 4**
---
<img width="1136" height="425" alt="image" src="https://github.com/user-attachments/assets/1951145c-49f6-4857-bf42-45b77929462f" />

```sql
--
SELECT grade, COUNT(*)
FROM customer
GROUP BY grade
HAVING grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York'
);
```

**Output:**

<img width="638" height="321" alt="image" src="https://github.com/user-attachments/assets/a5fcb3ea-2200-421f-80db-c21a12c2dfcd" />

**Question 5**
---
<img width="1076" height="600" alt="image" src="https://github.com/user-attachments/assets/13a85d03-b9c0-428e-968e-d234e1367f31" />

```sql
--
select id,name,age,city,income from Employee 
where age<(
      select avg(age) from Employee
      where income>1000000);
```

**Output:**

<img width="1111" height="322" alt="image" src="https://github.com/user-attachments/assets/f1c755b0-cc46-4496-b3c8-c01211856bcf" />

**Question 6**
---
<img width="956" height="614" alt="image" src="https://github.com/user-attachments/assets/ac2ce049-e1f9-4c3e-ba4a-91f65a7415ab" />

```sql
--
select * from CUSTOMERS
where SALARY=1500;
```

**Output:**

<img width="1128" height="309" alt="image" src="https://github.com/user-attachments/assets/90bd45e9-188c-42a4-b71b-3ae37d150f4d" />

**Question 7**
---
<img width="1138" height="544" alt="image" src="https://github.com/user-attachments/assets/f02185a5-a661-41bd-92ea-61bd74552764" />

```sql
--
SELECT student_id, student_name, subject, grade
FROM Grades
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades AS g
    WHERE g.subject = Grades.subject
);
```

**Output:**

<img width="1129" height="373" alt="image" src="https://github.com/user-attachments/assets/39077fe5-7963-40d3-af8f-eac5b3956a4e" />

**Question 8**
---
<img width="1139" height="501" alt="image" src="https://github.com/user-attachments/assets/c843458f-6135-446e-ba9e-bc185501131f" />

```

select ord_no,purch_amt,ord_date,customer_id,salesman_id from ORDERS
where purch_amt>(
      select avg(purch_amt ) from ORDERS
      where ord_date ='2012-10-10');
```

**Output:**
<img width="1120" height="367" alt="image" src="https://github.com/user-attachments/assets/b2fb3744-c84c-463f-8943-c24628222c05" />



**Question 9**
---
<img width="1032" height="596" alt="image" src="https://github.com/user-attachments/assets/acbcfa6e-b298-4893-99b5-0961507e995b" />

```sql
--
select *from CUSTOMERS
where id in(
      select ID from customers
      where address='Delhi' and age<30);
```

**Output:**

<img width="1125" height="310" alt="image" src="https://github.com/user-attachments/assets/ef3d4918-ded3-4d44-b3db-707d33fedc01" />

**Question 10**
<img width="1022" height="653" alt="image" src="https://github.com/user-attachments/assets/72daa4b8-c5ac-465e-825b-8f54c67470d9" />

```sql
--
select commission from salesman
where salesman_id in(
       select salesman_id from customer
       where city='Paris');
```

**Output:**

<img width="471" height="312" alt="image" src="https://github.com/user-attachments/assets/c5ede418-940a-4e3f-8be1-f312cbb4a966" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
