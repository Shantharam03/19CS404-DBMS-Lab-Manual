# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer
```
 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
```
Sample table: salesman
```
 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```

```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS "Salesman",
    s.city
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="948" height="616" alt="image" src="https://github.com/user-attachments/assets/df5c89b4-29b7-47bf-81e3-7709a383c4d8" />

**Question 2**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.

<img width="1141" height="450" alt="image" src="https://github.com/user-attachments/assets/a3e5f694-3587-4430-8ead-7d9ade90ec15" />

```sql
SELECT 
    c.cust_name
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt < 100;
```

**Output:**

<img width="552" height="411" alt="image" src="https://github.com/user-attachments/assets/63c2a2b4-f6ba-4942-bc76-4a990285ea79" />

**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.

<img width="1137" height="456" alt="image" src="https://github.com/user-attachments/assets/869a12e9-25b8-4b87-b182-6240a544d846" />

```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';

```

**Output:**

<img width="934" height="373" alt="image" src="https://github.com/user-attachments/assets/f0967acd-9b88-4c92-bb12-c11671d39e42" />

**Question 4**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.
<img width="1089" height="650" alt="image" src="https://github.com/user-attachments/assets/aebd9e23-06cd-4f63-b818-c267085a8322" />
<img width="625" height="266" alt="image" src="https://github.com/user-attachments/assets/10e0e4d5-c708-4e66-bd7b-06cc53be6afb" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS 'Order Amount',
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="932" height="613" alt="image" src="https://github.com/user-attachments/assets/ddd059b9-181a-4fd6-9a97-8818584568c4" />

**Question 5**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

<img width="1126" height="466" alt="image" src="https://github.com/user-attachments/assets/20471c51-1061-49c1-a50e-82e8dfa0e8cc" />

```
SELECT 
    s.name, 
    c.cust_name, 
    c.city, 
    c.grade, 
    c.salesman_id
FROM 
    salesman s
LEFT JOIN 
    customer c 
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.salesman_id IN (
        SELECT salesman_id
        FROM customer
        GROUP BY salesman_id
        HAVING COUNT(customer_id) > 1
    )
ORDER BY 
    s.name, c.grade;
```

**Output:**

<img width="937" height="525" alt="image" src="https://github.com/user-attachments/assets/c09d554f-ad5b-4acc-9907-a526083e8756" />

**Question 6**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

<img width="689" height="379" alt="image" src="https://github.com/user-attachments/assets/18a46e7d-547a-42c5-8a90-0352975d490a" />
<img width="604" height="273" alt="image" src="https://github.com/user-attachments/assets/71a44e24-b5a5-4d3a-bd8a-dcb474f8872d" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;
```

**Output:**

<img width="927" height="589" alt="image" src="https://github.com/user-attachments/assets/a16beee2-18c8-4f54-80ce-7dbc2ab68471" />

**Question 7**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.

<img width="1127" height="464" alt="image" src="https://github.com/user-attachments/assets/e30f70dc-0abe-4e48-8575-c8552acdbe9e" />

```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.discharge_date IS NULL;
```

**Output:**

<img width="707" height="415" alt="image" src="https://github.com/user-attachments/assets/225c0491-dc4c-4bd9-8cf6-ba6e058ac251" />

**Question 8**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.
<img width="667" height="387" alt="image" src="https://github.com/user-attachments/assets/cfb775ae-bb3e-4d74-a786-be307ab63b5b" />
<img width="827" height="595" alt="image" src="https://github.com/user-attachments/assets/6db1a8fb-32a9-4502-b48e-952f4fad0583" />

```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c ON o.customer_id = c.customer_id
INNER JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1122" height="625" alt="image" src="https://github.com/user-attachments/assets/810e1ac1-3cbf-4077-b7ee-a16274314285" />

**Question 9**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.

<img width="700" height="578" alt="image" src="https://github.com/user-attachments/assets/ae3d7b7a-a16c-4371-85a3-ca18efe14281" />

```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS "Salesman",
    s.city
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="934" height="603" alt="image" src="https://github.com/user-attachments/assets/efa69c45-d199-4246-95a5-4f4cfc63ab88" />

**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

<img width="1120" height="465" alt="image" src="https://github.com/user-attachments/assets/39c032fd-51ac-4215-bef7-47bb0074f9ff" />

```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="939" height="323" alt="image" src="https://github.com/user-attachments/assets/31b8cde3-3fbe-4524-9881-9f674d5bb85e" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
