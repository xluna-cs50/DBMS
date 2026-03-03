# DBMS
Initial Setup
SQL

CREATE DATABASE company_db;
USE company_db;
Practical-1
Perform the following: Create / Alter / Drop Table
Step 1: Create Table
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(20),
    marks INT
);
Step 2: Alter Table — Add Column
SQL

ALTER TABLE student ADD grade VARCHAR(2);
Step 3: Alter Table — Modify Column
SQL

ALTER TABLE student MODIFY name VARCHAR(50);
Step 4: Verify Structure
SQL

DESC student;
Step 5: Drop Table
SQL

DROP TABLE student;
Note: DROP TABLE deletes the table permanently.

Practical-2
Perform the following: Insert / Update / Select / Delete
Step 1: Create Table
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT,
    grade VARCHAR(2)
);
Step 2: Insert Records
SQL

INSERT INTO student (roll_no, name, marks, grade) VALUES (1, 'Amit', 85, 'A');
INSERT INTO student (roll_no, name, marks, grade) VALUES (2, 'Riya', 92, 'A+');
INSERT INTO student (roll_no, name, marks, grade) VALUES (3, 'Kunal', 78, 'B');
Important: Always specify column names to avoid column mismatch errors.

Step 3: Select (View All Records)
SQL

SELECT * FROM student;
Step 4: Update a Record
SQL

UPDATE student SET marks = 90 WHERE roll_no = 1;
Step 5: Verify Update
SQL

SELECT * FROM student;
Step 6: Delete a Record
SQL

DELETE FROM student WHERE roll_no = 2;
Step 7: Verify Deletion
SQL

SELECT * FROM student;
Practical-3
Perform the following: Sorting Data
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT,
    grade VARCHAR(2)
);

INSERT INTO student VALUES (1, 'Amit', 85, 'A');
INSERT INTO student VALUES (2, 'Riya', 92, 'A+');
INSERT INTO student VALUES (3, 'Kunal', 78, 'B');
INSERT INTO student VALUES (4, 'Sneha', 88, 'A');
Step 2: Sort in Ascending Order
SQL

SELECT * FROM student ORDER BY marks ASC;
Step 3: Sort in Descending Order
SQL

SELECT * FROM student ORDER BY marks DESC;
Step 4: Sort by Name Alphabetically
SQL

SELECT * FROM student ORDER BY name ASC;
Practical-4
Perform the following: Simple Queries with Aggregate Functions
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, 'Amit', 85);
INSERT INTO student VALUES (2, 'Riya', 92);
INSERT INTO student VALUES (3, 'Kunal', 78);
INSERT INTO student VALUES (4, 'Sneha', 88);
INSERT INTO student VALUES (5, 'Arjun', 95);
Step 2: COUNT — Total Number of Students
SQL

SELECT COUNT(*) FROM student;
Step 3: SUM — Total Marks
SQL

SELECT SUM(marks) FROM student;
Step 4: AVG — Average Marks
SQL

SELECT AVG(marks) FROM student;
Step 5: MAX — Highest Marks
SQL

SELECT MAX(marks) FROM student;
Step 6: MIN — Lowest Marks
SQL

SELECT MIN(marks) FROM student;
Practical-5
Perform the following: Dropping / Truncating / Renaming Tables
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, 'Amit', 85);
INSERT INTO student VALUES (2, 'Riya', 92);
Step 2: Truncate Table
SQL

TRUNCATE TABLE student;
Note: TRUNCATE deletes all records but keeps the table structure.

Step 3: Verify (Table exists but no data)
SQL

SELECT * FROM student;
DESC student;
Step 4: Rename Table
SQL

RENAME TABLE student TO students;
Step 5: Verify Rename
SQL

SHOW TABLES;
Step 6: Drop Table
SQL

DROP TABLE students;
Note: DROP deletes the table permanently (structure + data).

Practical-6
Perform the following: Upper / Lower / Initcap
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, 'amit', 85);
INSERT INTO student VALUES (2, 'RIYA', 92);
INSERT INTO student VALUES (3, 'kunal', 78);
Step 2: UPPER() — Convert to Uppercase
SQL

SELECT UPPER(name) FROM student;
Step 3: LOWER() — Convert to Lowercase
SQL

SELECT LOWER(name) FROM student;
Step 4: INITCAP() Equivalent in MySQL
Note: MySQL does not support INITCAP() directly. It is an Oracle function. In MySQL, we simulate it using UPPER(), LEFT(), LOWER(), and SUBSTRING().

SQL

SELECT
    CONCAT(
        UPPER(LEFT(name, 1)),
        LOWER(SUBSTRING(name, 2))
    ) AS Proper_Name
FROM student;
Explanation:

LEFT(name, 1) → takes the first letter
UPPER() → makes it capital
SUBSTRING(name, 2) → remaining letters from position 2
LOWER() → makes them lowercase
CONCAT() → joins everything together
Practical-7
Perform the following: Concat / Length / Substr
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, 'Amit', 85);
INSERT INTO student VALUES (2, 'Riya', 92);
INSERT INTO student VALUES (3, 'Kunal', 78);
Step 2: CONCAT() — Join Strings
SQL

SELECT CONCAT(name, ' scored ', marks) AS Result FROM student;
Step 3: LENGTH() — Find String Length
SQL

SELECT name, LENGTH(name) AS Name_Length FROM student;
Step 4: SUBSTR() — Extract Substring
SQL

SELECT name, SUBSTR(name, 1, 3) AS Short_Name FROM student;
Explanation: SUBSTR(name, 1, 3) extracts 3 characters starting from position 1.

Practical-8
Perform the following: Instr / Lpad / Rpad
Step 1: Create Table and Insert Data
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, 'Amit', 85);
INSERT INTO student VALUES (2, 'Riya', 92);
INSERT INTO student VALUES (3, 'Kunal', 78);
Step 2: INSTR() — Find Position of Character
SQL

SELECT name, INSTR(name, 'i') AS Position_of_i FROM student;
Explanation: Returns the position of the first occurrence of 'i' in the name. Returns 0 if not found.

Step 3: LPAD() — Left Padding
SQL

SELECT name, LPAD(name, 10, '*') AS Left_Padded FROM student;
Explanation: Pads the name with * on the left until total length is 10.

Step 4: RPAD() — Right Padding
SQL

SELECT name, RPAD(name, 10, '*') AS Right_Padded FROM student;
Explanation: Pads the name with * on the right until total length is 10.

Practical-9
Perform the following: Instr / Trim / Replace
Step 1: Create Table and Insert Data (with spaces)
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30),
    marks INT
);

INSERT INTO student VALUES (1, '   Amit   ', 85);
INSERT INTO student VALUES (2, 'Riya', 92);
INSERT INTO student VALUES (3, 'Kunal', 78);
Step 2: INSTR() — Find Position of Character
SQL

SELECT name, INSTR(name, 'a') AS Position_of_a FROM student;
Step 3: TRIM() — Remove Extra Spaces
SQL

SELECT name, TRIM(name) AS Trimmed_Name FROM student;
Explanation: Removes leading and trailing spaces. ' Amit ' becomes 'Amit'.

Step 4: REPLACE() — Replace Characters
SQL

SELECT name, REPLACE(name, 'a', 'X') AS Replaced_Name FROM student;
Important: MySQL is case-sensitive. REPLACE(name, 'A', 'X') replaces uppercase A only. Use lowercase 'a' to replace lowercase a.

Step 5: View All Transformations Together
SQL

SELECT
    name,
    TRIM(name) AS Trimmed,
    REPLACE(name, 'a', 'X') AS Replaced,
    INSTR(name, 'i') AS Pos_of_i
FROM student;
Practical-10
Perform the following: Abs() / Ceil() / Floor() / Mod()
Step 1: ABS() — Absolute Value
SQL

SELECT ABS(-10) AS Absolute_Value;
Result: 10

Step 2: CEIL() — Round Up
SQL

SELECT CEIL(4.3) AS Ceil_Value;
Result: 5

Step 3: FLOOR() — Round Down
SQL

SELECT FLOOR(4.8) AS Floor_Value;
Result: 4

Step 4: MOD() — Remainder
SQL

SELECT MOD(10, 3) AS Mod_Value;
Result: 1

Step 5: Using with Table Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT
);

INSERT INTO employee VALUES (1, 'Amit', -5000);
INSERT INTO employee VALUES (2, 'Riya', 7000);

SELECT name, salary, ABS(salary) AS Absolute_Salary FROM employee;
Practical-11
Perform the following: Pi() / Pow() / Sqrt() / Abs()
Step 1: PI() — Value of Pi
SQL

SELECT PI() AS Pi_Value;
Result: 3.141593

Step 2: POW() — Power
SQL

SELECT POW(2, 3) AS Power_Value;
Result: 8 (2³ = 8)

Step 3: SQRT() — Square Root
SQL

SELECT SQRT(25) AS Sqrt_Value;
Result: 5

Step 4: ABS() — Absolute Value
SQL

SELECT ABS(-15) AS Absolute_Value;
Result: 15

Step 5: All Functions Together
SQL

SELECT
    PI() AS Pi,
    POW(3, 2) AS Three_Squared,
    SQRT(49) AS Sqrt_49,
    ABS(-100) AS Abs_Neg100;
Practical-12
Perform the following using Arithmetic Operators in SQL
Step 1: Create Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT
);

INSERT INTO employee VALUES (1, 'Amit', 25000);
INSERT INTO employee VALUES (2, 'Riya', 30000);
INSERT INTO employee VALUES (3, 'Kunal', 28000);
Step 2: Addition (+)
SQL

SELECT name, salary, salary + 1000 AS Salary_After_Bonus FROM employee;
Step 3: Subtraction (-)
SQL

SELECT name, salary, salary - 2000 AS Salary_After_Deduction FROM employee;
Step 4: Multiplication (*)
SQL

SELECT name, salary, salary * 2 AS Double_Salary FROM employee;
Step 5: Division (/)
SQL

SELECT name, salary, salary / 12 AS Monthly_Salary FROM employee;
Step 6: Modulus (%)
SQL

SELECT name, salary, salary % 7 AS Remainder FROM employee;
Practical-13
Perform the following using Comparison Operators in SQL
Step 1: Create Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 25000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 30000, 'Mumbai');
INSERT INTO employee VALUES (3, 'Kunal', 28000, 'Delhi');
INSERT INTO employee VALUES (4, 'Sneha', 22000, 'Kerala');
Step 2: Equal (=)
SQL

SELECT * FROM employee WHERE city = 'Delhi';
Step 3: Not Equal (!=)
SQL

SELECT * FROM employee WHERE salary != 30000;
Step 4: Greater Than (>)
SQL

SELECT * FROM employee WHERE salary > 25000;
Step 5: Less Than (<)
SQL

SELECT * FROM employee WHERE salary < 28000;
Step 6: Greater Than or Equal (>=)
SQL

SELECT * FROM employee WHERE salary >= 25000;
Step 7: Less Than or Equal (<=)
SQL

SELECT * FROM employee WHERE salary <= 28000;
Practical-14
Logical Operators — AND
Step 1: Create Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 25000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 30000, 'Aligarh');
INSERT INTO employee VALUES (3, 'Kunal', 26000, 'Delhi');
INSERT INTO employee VALUES (4, 'Sneha', 25000, 'Kerala');
INSERT INTO employee VALUES (5, 'Arjun', 27000, 'Aligarh');
INSERT INTO employee VALUES (6, 'Meena', 24000, 'Delhi');
Query 1: Salary = 25000 AND city = Delhi
SQL

SELECT * FROM employee
WHERE salary = 25000 AND city = 'Delhi';
Query 2: Salary > 24000 AND city = Delhi
SQL

SELECT * FROM employee
WHERE salary > 24000 AND city = 'Delhi';
Query 3: Names with salary > 25000 AND city = Aligarh
SQL

SELECT name FROM employee
WHERE salary > 25000 AND city = 'Aligarh';
Query 4: IDs with salary > 20000 AND city = Delhi
SQL

SELECT emp_id FROM employee
WHERE salary > 20000 AND city = 'Delhi';
Query 5: Salary = 25000 AND city = Kerala
SQL

SELECT * FROM employee
WHERE salary = 25000 AND city = 'Kerala';
Query 6: Salary > 24000 AND < 39000 AND city = Delhi
SQL

SELECT * FROM employee
WHERE salary > 24000
AND salary < 39000
AND city = 'Delhi';
AND Operator Rule: Both conditions must be TRUE for the record to appear.

Condition 1	Condition 2	Result
TRUE	TRUE	Show
TRUE	FALSE	Not shown
FALSE	TRUE	Not shown
FALSE	FALSE	Not shown
Practical-15
Logical Operators — OR
Step 1: Create Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 25000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 30000, 'Aligarh');
INSERT INTO employee VALUES (3, 'Kunal', 26000, 'Delhi');
INSERT INTO employee VALUES (4, 'Sneha', 22000, 'Kerala');
INSERT INTO employee VALUES (5, 'Arjun', 27000, 'Aligarh');
INSERT INTO employee VALUES (6, 'Meena', 24000, 'Delhi');
Query 1: Salary = 25000 OR city = Delhi
SQL

SELECT * FROM employee
WHERE salary = 25000 OR city = 'Delhi';
Query 2: City = Kerala OR salary = 25000
SQL

SELECT * FROM employee
WHERE city = 'Kerala' OR salary = 25000;
Query 3: Salary > 25000 OR city = Delhi
SQL

SELECT * FROM employee
WHERE salary > 25000 OR city = 'Delhi';
Query 4: Names with salary > 25000 OR city = Aligarh
SQL

SELECT name FROM employee
WHERE salary > 25000 OR city = 'Aligarh';
Query 5: IDs with salary > 25000 OR city = Delhi
SQL

SELECT emp_id FROM employee
WHERE salary > 25000 OR city = 'Delhi';
OR Operator Rule: At least one condition must be TRUE for the record to appear.

Condition 1	Condition 2	Result
TRUE	TRUE	Show
TRUE	FALSE	Show
FALSE	TRUE	Show
FALSE	FALSE	Not shown
Practical-16
Logical Operators — NOT
Step 1: Create Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 25000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 30000, 'Mumbai');
INSERT INTO employee VALUES (3, 'Kunal', 28000, 'Delhi');
INSERT INTO employee VALUES (4, 'Sneha', 22000, 'Kerala');
INSERT INTO employee VALUES (5, 'Arjun', 30000, 'Aligarh');
Query 1: Employees who do NOT stay in Delhi
Method 1 — Using NOT:

SQL

SELECT * FROM employee
WHERE NOT city = 'Delhi';
Method 2 — Using != (simpler):

SQL

SELECT * FROM employee
WHERE city != 'Delhi';
Query 2: Employees who don't have salary 30000
Method 1 — Using NOT:

SQL

SELECT * FROM employee
WHERE NOT salary = 30000;
Method 2 — Using != (simpler):

SQL

SELECT * FROM employee
WHERE salary != 30000;
NOT Operator Rule: Reverses the condition. If condition is TRUE, NOT makes it FALSE and vice versa.

Practical-17
Logical Operators — BETWEEN
Step 1: Create Employee Table and Insert Data
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 4000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 7000, 'Mumbai');
INSERT INTO employee VALUES (3, 'Kunal', 10000, 'Delhi');
INSERT INTO employee VALUES (4, 'Sneha', 12000, 'Kerala');
INSERT INTO employee VALUES (5, 'Arjun', 3500, 'Aligarh');
INSERT INTO employee VALUES (6, 'Meena', 6000, 'Delhi');
Query 1: Salary BETWEEN 3500 and 11000
SQL

SELECT * FROM employee
WHERE salary BETWEEN 3500 AND 11000;
Note: BETWEEN is inclusive — it includes both 3500 and 11000.

Query 2: Salary NOT BETWEEN 3500 and 6500
SQL

SELECT * FROM employee
WHERE salary NOT BETWEEN 3500 AND 6500;
Shows employees with salary < 3500 OR salary > 6500.

Step 2: Create Customer Table and Insert Data
SQL

CREATE TABLE customer (
    customer_id INT PRIMARY KEY,
    name VARCHAR(30),
    age INT,
    city VARCHAR(30)
);

INSERT INTO customer VALUES (1, 'Rahul', 22, 'Delhi');
INSERT INTO customer VALUES (2, 'Priya', 28, 'Mumbai');
INSERT INTO customer VALUES (3, 'Neha', 19, 'Kerala');
INSERT INTO customer VALUES (4, 'Rohan', 31, 'Delhi');
INSERT INTO customer VALUES (5, 'Simran', 25, 'Aligarh');
Query 3: Customers with age > 20 AND < 30
SQL

SELECT name FROM customer
WHERE age > 20 AND age < 30;
Alternative using BETWEEN:

SQL

SELECT name FROM customer
WHERE age BETWEEN 21 AND 29;
Practical-18
Perform the following using Set Operators in SQL
Step 1: Create Two Tables
SQL

CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee VALUES (1, 'Amit', 25000, 'Delhi');
INSERT INTO employee VALUES (2, 'Riya', 30000, 'Mumbai');
INSERT INTO employee VALUES (3, 'Kunal', 28000, 'Delhi');

CREATE TABLE employee2 (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary INT,
    city VARCHAR(30)
);

INSERT INTO employee2 VALUES (4, 'Sneha', 22000, 'Kerala');
INSERT INTO employee2 VALUES (5, 'Rahul', 35000, 'Delhi');
INSERT INTO employee2 VALUES (2, 'Riya', 30000, 'Mumbai');
Step 2: UNION — Removes Duplicates
SQL

SELECT name FROM employee
UNION
SELECT name FROM employee2;
Note: Riya appears in both tables but will be shown only once.

Step 3: UNION ALL — Keeps Duplicates
SQL

SELECT name FROM employee
UNION ALL
SELECT name FROM employee2;
Note: Riya will appear twice.

Practical-19
Perform the following Join Queries
Part A: INNER JOIN
Step 1: Create customer1 Table
SQL

CREATE TABLE customer1 (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(30),
    city VARCHAR(30)
);

INSERT INTO customer1 VALUES (1, 'Amit', 'Delhi');
INSERT INTO customer1 VALUES (2, 'Riya', 'Mumbai');
INSERT INTO customer1 VALUES (3, 'Kunal', 'Aligarh');
Step 2: Create orders Table
SQL

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    amount INT
);

INSERT INTO orders VALUES (101, 1, '2024-01-10', 5000);
INSERT INTO orders VALUES (102, 2, '2024-02-15', 3000);
INSERT INTO orders VALUES (103, 1, '2024-03-20', 7000);
INSERT INTO orders VALUES (104, 4, '2024-04-05', 2000);
Note: customer_id 4 does NOT exist in customer1 — helps demonstrate join behavior.

Query 1: INNER JOIN — All Details
SQL

SELECT *
FROM orders
INNER JOIN customer1
ON orders.customer_id = customer1.customer_id;
Shows only records where customer_id matches in both tables.

Query 2: INNER JOIN — Without Repeating Common Columns
SQL

SELECT
    orders.order_id,
    orders.order_date,
    orders.amount,
    customer1.customer_name,
    customer1.city
FROM orders
INNER JOIN customer1
ON orders.customer_id = customer1.customer_id;
Part B: LEFT OUTER JOIN
Step 3: Create department Table
SQL

CREATE TABLE department (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(30)
);

INSERT INTO department VALUES (1, 'HR');
INSERT INTO department VALUES (2, 'IT');
INSERT INTO department VALUES (3, 'Finance');
INSERT INTO department VALUES (5, 'Marketing');
Step 4: Create employees Table
SQL

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    dept_id INT
);

INSERT INTO employees VALUES (1, 'Amit', 1);
INSERT INTO employees VALUES (2, 'Riya', 2);
INSERT INTO employees VALUES (3, 'Kunal', 4);
INSERT INTO employees VALUES (4, 'Sneha', 3);
Note: dept_id 4 does NOT exist in department. dept_id 5 has no employee.

Query 3: LEFT OUTER JOIN — All Details
SQL

SELECT *
FROM employees
LEFT JOIN department
ON employees.dept_id = department.dept_id;
Shows ALL employees. If no matching department, department columns show NULL.

Query 4: LEFT JOIN — Without Repeating Common Columns
SQL

SELECT
    employees.emp_id,
    employees.name,
    department.dept_name
FROM employees
LEFT JOIN department
ON employees.dept_id = department.dept_id;
Part C: RIGHT OUTER JOIN
Query 5: RIGHT JOIN (Employees left, Department right) — Without Repeating Common Columns
SQL

SELECT
    employees.emp_id,
    employees.name,
    department.dept_id,
    department.dept_name
FROM employees
RIGHT JOIN department
ON employees.dept_id = department.dept_id;
Shows ALL departments. If no matching employee, employee columns show NULL.

Step 5: Create borrower and loans Tables
SQL

CREATE TABLE borrower (
    borrower_id INT PRIMARY KEY,
    customer_name VARCHAR(30)
);

INSERT INTO borrower VALUES (1, 'Rahul');
INSERT INTO borrower VALUES (2, 'Priya');
INSERT INTO borrower VALUES (3, 'Neha');

CREATE TABLE loans (
    loan_id INT PRIMARY KEY,
    borrower_id INT,
    amount INT
);

INSERT INTO loans VALUES (101, 1, 50000);
INSERT INTO loans VALUES (102, 2, 70000);
INSERT INTO loans VALUES (103, 4, 90000);
Query 6: RIGHT JOIN (Loans left, Borrower right) — Without Repeating Common Columns
SQL

SELECT
    loans.loan_id,
    loans.amount,
    borrower.borrower_id,
    borrower.customer_name
FROM loans
RIGHT JOIN borrower
ON loans.borrower_id = borrower.borrower_id;
Part D: FULL OUTER JOIN
Important: MySQL does NOT support FULL OUTER JOIN directly. We simulate it using LEFT JOIN + UNION + RIGHT JOIN.

Query 7: FULL OUTER JOIN (Loans & Borrower)
SQL

SELECT
    loans.loan_id,
    loans.borrower_id,
    borrower.customer_name,
    loans.amount
FROM loans
LEFT JOIN borrower
ON loans.borrower_id = borrower.borrower_id

UNION

SELECT
    loans.loan_id,
    loans.borrower_id,
    borrower.customer_name,
    loans.amount
FROM loans
RIGHT JOIN borrower
ON loans.borrower_id = borrower.borrower_id;
Query 8: FULL OUTER JOIN (Employees & Department)
SQL

SELECT
    employees.emp_id,
    employees.name,
    department.dept_name
FROM employees
LEFT JOIN department
ON employees.dept_id = department.dept_id

UNION

SELECT
    employees.emp_id,
    employees.name,
    department.dept_name
FROM employees
RIGHT JOIN department
ON employees.dept_id = department.dept_id;
Part E: CROSS JOIN
Query 9: CROSS JOIN (Borrower & Department)
SQL

SELECT *
FROM borrower
CROSS JOIN department;
Explanation: Produces a Cartesian Product. If borrower has 3 rows and department has 4 rows, result will have 3 × 4 = 12 rows.

Part F: NATURAL JOIN
Step 6: Create borewell Table
SQL

CREATE TABLE borewell (
    bore_id INT PRIMARY KEY,
    loan_id INT,
    location VARCHAR(30)
);

INSERT INTO borewell VALUES (1, 101, 'Delhi');
INSERT INTO borewell VALUES (2, 102, 'Mumbai');
Query 10: NATURAL JOIN (Borewell & Loans)
SQL

SELECT *
FROM borewell
NATURAL JOIN loans;
Explanation: Automatically joins on the common column (loan_id). The common column appears only once in the result.

Join Types Summary
Join Type	What It Shows
INNER JOIN	Only matching rows from both tables
LEFT JOIN	All left table rows + matching right rows
RIGHT JOIN	All right table rows + matching left rows
FULL JOIN	All rows from both tables
CROSS JOIN	Cartesian product of both tables
NATURAL JOIN	Auto-join on common column names
Practical-20
Perform the following: Views
Step 1: Create borrower Table (if not already created)
SQL

CREATE TABLE borrower (
    borrower_id INT PRIMARY KEY,
    customer_name VARCHAR(30)
);

INSERT INTO borrower VALUES (1, 'Rahul');
INSERT INTO borrower VALUES (2, 'Priya');
INSERT INTO borrower VALUES (3, 'Neha');
Step 2: Create View V1 — Entire Table
SQL

CREATE VIEW V1 AS
SELECT * FROM borrower;
Step 3: View V1
SQL

SELECT * FROM V1;
Step 4: Create View V2 — Only ID and Name
SQL

CREATE VIEW V2 AS
SELECT borrower_id, customer_name
FROM borrower;
Step 5: View V2
SQL

SELECT * FROM V2;
Step 6: List All Views in Database
SQL

SHOW FULL TABLES WHERE Table_type = 'VIEW';
Step 7: Delete View V3
SQL

DROP VIEW IF EXISTS V3;
Note: IF EXISTS prevents error if V3 doesn't exist.

Practical-21
Perform the following: Constraints
Step 1: Create student Table with Constraints
SQL

CREATE TABLE student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    age INT CHECK (age >= 18),
    email VARCHAR(50) UNIQUE,
    city VARCHAR(30) DEFAULT 'Delhi'
);
Constraints Used:

Constraint	Description
PRIMARY KEY	Uniquely identifies each record
NOT NULL	Column cannot have NULL values
CHECK	Validates data (age must be ≥ 18)
UNIQUE	No duplicate values allowed
DEFAULT	Sets default value if none provided
Step 2: Create courses Table with Foreign Key
SQL

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(30) NOT NULL,
    duration INT CHECK (duration > 0),
    roll_no INT,
    FOREIGN KEY (roll_no) REFERENCES student(roll_no)
);
Foreign Key: roll_no in courses must exist in student table.

Step 3: Insert Sample Data
SQL

INSERT INTO student VALUES (1, 'Amit', 20, 'amit@gmail.com', 'Mumbai');
INSERT INTO student VALUES (2, 'Riya', 22, 'riya@gmail.com', DEFAULT);

INSERT INTO courses VALUES (101, 'Data Science', 6, 1);
INSERT INTO courses VALUES (102, 'SQL', 3, 2);
Step 4: Verify Data
SQL

SELECT * FROM student;
SELECT * FROM courses;
Step 5: Test Constraints (These Will Cause Errors)
Duplicate Primary Key:

SQL

-- This will FAIL
INSERT INTO student VALUES (1, 'Kunal', 19, 'kunal@gmail.com', 'Delhi');
Error: Duplicate entry for primary key.

NULL in NOT NULL column:

SQL

-- This will FAIL
INSERT INTO student VALUES (3, NULL, 19, 'abc@gmail.com', 'Delhi');
Error: Column 'name' cannot be null.

Foreign Key Violation:

SQL

-- This will FAIL
INSERT INTO courses VALUES (103, 'Python', 4, 10);
Error: roll_no 10 does not exist in student table.

CHECK Constraint Violation:

SQL

-- This will FAIL (in supported MySQL versions)
INSERT INTO student VALUES (4, 'Test', 15, 'test@gmail.com', 'Delhi');
Error: age must be ≥ 18.

Quick Reference — How to Execute Commands in MySQL
Starting MySQL
text

1. Open MySQL Command Line Client
2. Enter your password
3. Select database:
SQL

SHOW DATABASES;
USE your_database_name;
Execution Rules
Always end every command with a semicolon (;)
Press Enter to execute
If correct → Query OK
If error → Check spelling and syntax
Execute one query at a time
Recommended Order for Practicals
Create database / Use database
Create table
Insert records
Perform operations (SELECT, UPDATE, functions, joins, etc.)
Drop table at end (if needed)
