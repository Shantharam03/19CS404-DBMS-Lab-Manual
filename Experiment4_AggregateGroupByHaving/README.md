# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many appointments are scheduled for each doctor?


```sql
select DoctorID,count(*) as TotalAppointments from Appointments
group by DoctorID
```

**Output:**

<img width="1128" height="491" alt="image" src="https://github.com/user-attachments/assets/fc8c7b0f-03d8-4c7d-9b98-b38fb0fcb794" />

**Question 2**
---
What is the most common diagnosis among patients?


```sql
select Diagnosis , count(*) as DiagnosisCount from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC
limit 1
```

**Output:**

<img width="943" height="437" alt="image" src="https://github.com/user-attachments/assets/9dcc73ed-8caf-4f32-856a-1cdd433121a8" />

**Question 3**
---
How many male and female doctors are there in each medical specialty?


```sql
SELECT Specialty   ,       Gender  , count(*) as TotalDoctors from Doctors
group by Specialty, Gender
```

**Output:**

<img width="785" height="490" alt="image" src="https://github.com/user-attachments/assets/a63d2844-1c0b-4238-a128-e00b39b1db2d" />

**Question 4**
---
Write a SQL query to find the customer with longest name?


```sql
SELECT name , LENGTH(name) as "length" from customer
order by "length" DESC
limit 1
```

**Output:**

<img width="732" height="268" alt="image" src="https://github.com/user-attachments/assets/e09895c7-77c3-4f25-94c5-20b7f4bb2e51" />

**Question 5**
---
Write a SQL query to find the total number of unique cities in the customer table?


```sql
SELECT count(DISTINCT city) as unique_cities from customer
```

**Output:**

<img width="690" height="275" alt="image" src="https://github.com/user-attachments/assets/af5f4eba-547a-4439-ba7b-0cd30bc439bc" />


**Question 6**
---
Write a SQL query to find how many employees have an income greater than 50K?


```sql
select count(income) as employees_count from employee
where income>=50000
```

**Output:**

<img width="680" height="263" alt="image" src="https://github.com/user-attachments/assets/da740d6b-7d79-4ba3-9a25-3b1ec51ad60c" />

**Question 7**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id



```sql
select count(distinct salesman_id) as "COUNT" from orders
```

**Output:**

<img width="836" height="272" alt="image" src="https://github.com/user-attachments/assets/c2837711-6447-42cf-a832-a64dfcadcb09" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.


```sql
select age,MIN(income) as "MIN(income)" from employee
group by age
having "MIN(income)"<400000
```

**Output:**

<img width="924" height="313" alt="image" src="https://github.com/user-attachments/assets/cf0d6cca-20e0-4e88-8420-e1d0edf0206c" />

**Question 9**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.


```sql
select address, SUM(salary) as "SUM(salary)" from customer1
group by address 
having "SUM(salary)">2000
```

**Output:**

<img width="677" height="388" alt="image" src="https://github.com/user-attachments/assets/45f36271-6b7a-48fa-91db-237ceb79170f" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.


```sql
select age, min(income) as Income from employee
group by age
having Income<1000000
```


**Output:**

<img width="691" height="390" alt="image" src="https://github.com/user-attachments/assets/7ce27712-352c-4e25-a483-714ff6f4daf5" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
