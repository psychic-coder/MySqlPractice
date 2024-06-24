This is a mysql playtime repo::----

we can even write the queries in small alphabets

!!Remember--> we have to give semi-colon after after every query 

//we write the query in the sqlfile
cmd(it shows all the databases present)->SHOW DATABASES;
cmd(to create a database)->CREATE DATABASE name_database;
cmd(working with a database, as this takes us inside of school_db database)->USE name_db;
cmd(to know the current database we're working in)-->SELECT DATABASE();
cmd(Deleting a database)-->DROP DATABASE name_db;
cmd(Creating a new Table)-->CREATE TABLE students(
                                             id INT,
                                             name VARCHAR(100)
                                            );
cmd(To see your table in a database )-->DESC table_name;
cmd(To insert data in a table)-->INSERT INTO table_name (id,name) VALUES (101,"ROHIT");
cmd(if we're inserting the data in the same order as the cols then we're not needed to write the coloumn name)-->INSERT INTO table_name VALUES (101,"ROHIT");
cmd(inserting multiple values to the table)->INSERT INTO students VALUES (102,"Raju",10),(104,"sham",7);
cmd(reading datas from tables)-->SELECT * FROM <table_name>; SELECT <coloumn_name> * students;
ex:--> SELECT id,name FROM students;
cmd(get data on the basis of given condition)-->SELECT name FROM students WHERE id=102;
SELECT * FROM students WHERE id=102;
cmd(Modify and update data from a table)-->UPDATE students SET contacts=132415 WHERE name="sham";
cmd(disable safe updates mode for your session by executing)-->SET SQL_SAFE_UPDATES = 0;
cmd(deleting data from a table)-->DELETE FROM students WHERE name="sham";
cmd(deleting table from a database )-->DROP TABLE students;
cmd("what is NOT NULL")-->CREATE TABLE customers1(
    id INT NOT NULL,
    name VARCHAR(100) NOT NULL
);
cmd("DEFAULT keyword")--> CREATE TABLE employee(name VARCHAR(100),acc_type VARCHAR(50) DEFAULT "savings");
in the above query we gave the default value of acc_type "savings" so even if we don't give the value for account type in data it will be saved as "savings"

what is primarykey->PRIMARY KEY constraint quickly identifies each record in a table , it must be unique and not null , one can have only one primary key.
cmd("primary key")-->CREATE TABLE customers(
    acc_no INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    acc_type VAR_CHAR(50) NOT NULL DEFAULT "Savings"
)
cmd(AUTO_INCREMENT,by default it starts from 1)-->CREATE TABLE customers5(
    acc_no INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    acc_type VARCHAR(50) NOT NULL DEFAULT "Savings" 
)
cmd(ALIAS keyword)-->SELECT acc_no AS "Account No." FROM customers;//for single col
SELECT acc_no AS "Account No.",name as "Customer Name" FROM customers4;//for multiple cols

cmd (CONCAT string function)-> CONCAT(first_col,sec_col) or CONCAT(first_word,sec_word,...)
ex:--> SELECT CONCAT("Hey","Buddy!")-->output-->"HeyBuddy"
ex:--> SELECT CONCAT("Hey","Buddy!","Hello")-->output-->"HeyBuddy!Hello"
inplace of the words we can even give spacing 

Usecase:--> SELECT emp_id,CONCAT(fname,lname) as FULLName FROM employees;
//we can even give spacing between fname and lname values in fullName
Usecase:--> SELECT emp_id,CONCAT(fname,lname) as FULLName FROM employees;
//in the below example the ABCD will be added to the fname
Usecase:--> SELECT emp_id,CONCAT(fname,"ABCD") as NewName FROM employees;

cmd (CONCAT_WS is a  string function,where WS stands for with seperator)-->
CONCAT_WS("-",fname,lname)

ex:-->SELECT CONCAT_WS("-","hi","HELLO"),OUTPUT-->hi-HELLO
ex:-->SELECT CONCAT_WS("-","hi","HELLO","Jim"),OUTPUT-->hi-HELLO-Jim
ex:-->SELECT CONCAT_WS(":",emp_id,fname,desig) as NewData FROM employees 

cmd(SUBSTRING command)-->ex:-
SELECT SUBSTRING("Hey buddy",1,4);-->output-->Hey
SELECT SUBSTRING("Hey buddy",-3);-->output-->ddy

ex:-->
SELECT SUBSTRING(emp_id,2) AS EmpId,fname FROM employees;//over here 2 represents the starting index

cmd(REPLACE) ex:--> REPLACE(str,from_str,to_str)
REPLACE("Hey_Buddy","Hey","Hello")
ex:-->SELECT REPLACE(emp_id,10,1000) AS NewEmpIDs,fname FROM employees;

cmd("REVERSE")-->
SELECT REVERSE("Hello");

ex:--> SELECT REVERSE(emp_id) AS NEWId FROM employees;

cmd("UPPER","LOWER")--> SELECT LOWER("UYKFGK");-->out-->uykfgk
SELECT emp_id,UPPER(fname) AS MOD from employees;

cmd("CHAR_LENGTH")-->SELECT CHAR_LENGTH("OK BRO")
ex:-->SELECT fname,CHAR_LENGTH(fname) as Length FROM employees;

//in the below we're gettin the data of the employees where the fname is greater then 5
ex:-->SELECT * FROM employess WHERE CHAR_LENGTH(fname)>5;

cmd("INSERT")ex:-
5--> staring index of insertion, raju is the word we want to insert
SELECT INSERT("Hey Wassup",5,0,"Raju ");output:--->Hey Raju Wassup


cmd("LEFT")ex:-ITS USED FOR  TRIM FROM LEFT
SELECT LEFT("Hey Buddy",2);-->output-->"y Buddy"

cmd("RIGHT")EX:-ITS USED FOR  TRIM FROM RIGHT
SELECT RIGHT("Hey Buddy",2);-->output-->"Hey Bud"

cmd("REPEAT")ex:-->
Hello is the word we want to repeat and 2 is the number of times we want to repeat
SELECT REPEAT("HELLO" 2);-->output-->HELLO HELLO


cmd("TRIM"),its used for removing the extra spaces from the end and the start
SELECT TRIM(" Alright! ");,ex:-"Alright!"


multiple function use ex:-->
SELECT CONCAT_WS(":",emp_id,CONCAT(fname," ",lname),desig,dept) FROM employees;

cmd(DISTINCT keyword):-->the distinct keyword will return each value only once 
SELECT DISTINCT dept FROM employees;ex::-->it will return all the distict departments we have

SELECT DISTINCT fname,lname FROM employees; :->in this example we used the distinct keyword on the combined values of fname and lname, it combined the fname and lname values and returned us the fullName which is not repeated

cmd(ORDER BY keyword):--> it is basically used for sorting the table

SELECT * FROM employees ORDER BY fname;-->this query will sort the data on the basis of the fname . by default it will sort in ascending order

SELECT * FROM employees ORDER BY fname DESC;--> this will sort the data in the descending order

SELECT dept,fname FROM employees ORDER BY dept,fname; -->this will sort the data first on the basis of dept and then alike words in dept will be sorted on the basis of the sub category which is fname;


cmd(LIKE keyword)-->
SELECT * FROM employees WHERE dept LIKE "%Acc%";::-->within the modulus we give the first few letters of the word on the basis of what we want to search and upper and lower case dosen't matter

SELECT * FROM employees WHERE fname LIKE "____";---->in this case we're searching for the data where the fname is 4 characters long, for 4 characters we have to give the dash"_" 4 times


cmd(LIMIT keyword)-->
SELECT * FROM employees LIMIT 5;(it will give the first 5 values of the table) 
SELECT * FROM employees LIMIT 3,3;(it will give the data from 4th row to the 3rd count) 

SELECT * FROM employees ORDER BY salary DESC LIMIT 1;-->it will give the data of the person with the highest salary

cmd(COUNT)-->
SELECT COUNT(*) FROM employees;->it gives the number of employees
SELECT COUNT(DISTINCT dept) FROM employees;-->it will give the number of distinct departments 
SELECT COUNT(emp_id) FROM employees WHERE desig="Manager";-->we're getting the totalnumber of employees where the desig is of manager,

cmd(GROUP BY)WE group the data on the basis of a particular data:-->

ex:-->the below code will grp the data on the basis of department
SELECT dept FROM employees GROUP BY dept;

//in this example we're grouping the employees on the basis of department , and we're counting the nuber of employees in each department
SELECT dept,COUNT(emp_id) FROM employees GROUP BY dept;

cmd(MAX and MIN) from employees:-->
SELECT MAX(age) FROM employees;-->it will return the max salary
SELECT MIN(age) FROM employees;

Subqueries:---->
we're fetching all the details for the employee with the maximum salary
SELECT emp_id,fname,salar FROM employees WHERE salary=(SELECT MAX(SALARY) FROM employees);

cmd(SUM & AVG):-->
SELECT SUM(salary) FROM employees;
SELECT AVG(salary) FROM employees;

we're fetching the total sum of the salaries in each group and we're also counting the number of people in each department 
SELECT dept,SUM(salary),COUNT(emp_id) FROM employees GROUP BY dept;

dataType(DECIMAL)--->
Ex:-in the below example 5 is the total number of digits including the decimal  and 2 is the digits present after decimal
DECIMAL keyword-DECIMAL(5,2)
CREATE TABLE num1(
    price DECIMAL(5,2)
);

dataType(FLOAT,DOUBLE)
FLOAT takes upto total 7 digits ,
DOUBLE takes upto total 15 digits
create table num2(
    f float,
    d double
);

dataType(DATE,TIME,DATETIME):--->
DATE FORMAT-->YYYY-MM-DD FORMAT
TIME FORMAT--> HH:MM:SS FORMAT
DATETIME-->"yyyy-mm-dd HH:MM:SS" FORMAT

CREATE TABLE PERSON(
    D DATE,
    T TIME,
    DT DATETIME
);

CURDATE ,CURTIME, NOW -->functions
CURDATE()--OUTPUT->YYYY-MM-DD
CURTIME()--OUTPUT->HH:MM:SS
NOW()--OUTPUT->YYYY-MM-DD hh:mm:ss

INSERT INTO PERSON(D,T,DT) VALUES(CURDATE(),CURTIME(),NOW());



Functions for DATE TIME
DAYNAME,DAYMONTH,DAYOFWEEK

SELECT DAYNAME("2007-02-03");--OUTPUT-->"Saturday"
SELECT DAYOFMONTH("2007-02-03");--OUTPUT-->3
SELECT DAYOFWEEK("2007-02-03");--OUTPUT-->7

we can also use the above in the below way:-->
SELECT DAYNAME(CURDATE());
SELECT DAYOFMONTH(CURDATE());
SELECT DAYOFWEEK(CURDATE());


SELECT MONTHNAME(CURDATE());--->June

SELECT jt,HOUR(jt) FROM PERSON ;-->HOUR is used for taking only the value of the hour from the time
SELECT jt,MINUTE(jt) FROM PERSON ;-->MINUTE is used for taking only the value of the MINUTE from the time

DATE_FORMAT()--->IT IS USED TO FORMAT THE DATE
ex:-%D gives the date of the month,%a gives the weekday and %T dives the time
DATE_FORMAT(NOW(),"%D %a at %T")-->
RESULT:21st Tue at 21:20:28

DATE_FORMAT(NOW(),"%m/%d/%y")-->
RESULT:04/16/23

SELECT jdt,DATE_FORMAT(jdt,"%D %a at %k") FROM person;

DATE_FORMAT(now(),"%H:%i")-->
output-->RESULT:20:34

DATE_FORMAT(dob,"%r")-->
output-->RESULT: 08:35:48 PM

function for (DATE MATHS)
DATEDIFF(expr1,expr2)-->it gives the difference between two datesnitreturns the values in the form of dates
ex:-->DATEDIFF("2023-04-20","2023-03-15")


DATE_ADD(date,INTERVAL expr unit)
DATE_SUB(date,INTERVAL expr unit)
ex:-->DATE_ADD("2023-05-01",INTERVAL 1 DAY)
ex:-->DATE_ADD("2023-05-01",INTERVAL 1 YEAR)
ex:-->DATE_SUB("2023-05-01",INTERVAL 1 MONTH)

TIMEDIFF(expr1,expr2);
TIMEDIFF("20:00:00","12:00:00");


DEFAULT & ON UPDATE TIMESTAMP
CREATE TABLE BLOGS(
    id INT PRIMARY KEY,
    text VARCHAR(150),
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,//this will work when we create the data
    updated_at DATETIME ON UPDATE CURRENT_TIMESTAMP //this will work when the data will be updated
);

UPDATE BLOGS 
SET text="fuheabub"
WHERE id="101";

CHAR dataType is mostly preferred when we want to keep the number of characters to be the same

SELECT DATE_FORMAT(NOW(),"%M %D at %T");--output-->
April 21st at 22:42:50;

Relational Operators
>,<,>=,<=,!=,=

Logical Operators
AND , OR

ex:->
SELECT * FROM Employees WHERE salary=25000 AND dept="Loan";
SELECT * FROM Employees WHERE salary=25000 OR dept="Loan";

Use of IN & NOT IN 
ex:-->in this example if in the dept if any of the value is matched we get the result
SELECT * FROM employees 
WHERE dept IN("Account","Cash","Loan");

ex:-->in the below example we're asking for all the data except Account,Cash and Loan
SELECT * FROM employees 
WHERE dept NOT IN("Account","Cash","Loan");

cmd(BETWEEN keyword)-->
its similar to 
SELECT * FROM employess WHERE salary>25000 AND salary<65000;
Between works in the similar way
SELECT * FROM employess WHERE salary BETWEEN 23000 AND 40000;

cmd (CASE statement)
ex1:-->in the below code we're fetching fname,salary and an extra column in the table called Salary Category in which we're marking each user "Higher Salary" and "Lower Salary" in the table on the basis of the salary greater then equal to 50000

SELECT fname,salary,
        CASE
        WHEN salary>=50000 THEN "Higher Salary"
        ELSE "Low Salary"
        END 
        AS "Salary Category"
        FROM employees;

 ex2:-->
 ELECT fname,salary,
        CASE
        WHEN salary>=50000 THEN "Higher Salary"
        WHEN salary>=30000 AND salary<50000 THEN "Mid Salary"
        ELSE "Low Salary"
        END 
        AS "Salary Category"
        FROM employees       


cmd(IS):-->
In this code we're searching for data's where the coloumn jt has a null values
SELECT * FROM person WHERE jt IS NULL

cmd(NOT LIKE)-->
ex:-in th below code we're are looking for the names not starting with A
SELECT * FROM employees WHERE fname NOT LIKE "A%";

cmd(UNIQUE)--->
it is used to make the data unique in a field
ex:-->
CREATE TABLE contact(
    mob INT UNIQUE
);

cmd(CHECK)-->it is used to check on the basis of the constraint 
ex:-->in the below code we're checking whether the value of the mob we're entering is equal to 10 or not
CREATE TABLE contact1(
    mob VARCHAR(15) UNIQUE CHECK (LENGTH(mob)=10)
);


NAMED CONSTRAINT

ex:-->in the below example we gave a name to the constraint "mob_no_less_than_10digits" and then we give the condition
CREATE TABLE contacts(
    name VARCHAR(50),
    mob VARCHAR(15) UNIQUE,
    CONSTRAINT mob_no_less_than_10digits CHECK (LENGTH(mob)>=10)
);


cmd(ALTER)--->its is used to alter the data or coloumn in a table
EX:->
ALTER TABLE contacts
ADD COLUMN city VARCHAR(50);

Deleting a coloumn
ex:->
ALTER TABLE contacts
DROP COLUMN city;

Changing the name of the coloumn
ex:->
ALTER TABLE contacts
RENAME COLUMN emp_id TO id;

Renaming a table
ex:-->
ALTER TABLE contacts
RENAME TO mycontacts;

Changing the data type of a coloumn in a table
ex:->
ALTER TABLE contacts
MODIFY mob VARCHAR(15) DEFAULT "unknown"; 

JOINS in Table
Types of Relationship
1:1-->1 row in the first table is linked to exactly one row in the second table
1:many-->1 row in the first table is linked to more than 1 row in the next tablw
many:many-->more than one row in the first table is linked to more than 1 row in the next table

ex:-->in the below code the customers table is connected to the orders table using the foreign key

CREATE TABLE customers(
    cust_id AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(50)
);

CREATE TABLE orders(
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    date DATE DEFAULT CURRENT_TIMESTAMP,
    amount DECIMAL(10,2),
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customers(cust_id)
);

INSERT INTO customers(name,email) VALUES ("Hello","rohit@gmail.com");
INSERT INTO orders(amount,cust_id) VALUES (22000,1);//we're connecting this row to one row of the table one

JOIN operation is used to combine rows from two or more tables based on a related column between them.
Types of JOIN

Cross Join-->every row in one table is connected with every row from another table
SELECT * FROM customers,orders;

Inner Join-->returns only the rows where there is a match between the specified coloumns in both the left (or first) and right (or second) tables.
ex:->
SELECT * FROM customers 
INNER JOIN orders 
ON orders.cust_id=customers.cust_id;

ex:-->in the below code we're grouping the users on the basis of their name and getting the amount of purchases they have made
SELECT name,SUM(amount) FROM customers 
INNER JOIN orders 
ON orders.cust_id=customers.cust_id;
GROUP BY name;

Left Join-->Returns all rows from the left table and the matching rows from the right table, 
ex:-->customers is the left table and orders is the right table
SELECT * FROM customers
LEFT JOIN orders
ON orders.cust_id=customers.cust_id;

ex:-->customers is the left table and orders is the right table
SELECT name,SUM(amount) FROM customers
LEFT JOIN orders
ON orders.cust_id=customers.cust_id GROUP BY name;

ex:-->customers is the left table and orders is the right table
and we also added the ifnull condition that if the amount is null we make the amount value will be 0
SELECT name,IFNULL(SUM(amount),0) FROM customers
LEFT JOIN orders
ON orders.cust_id=customers.cust_id GROUP BY name;


Right Join-->Returns all rows from the right table and the matching rows from the left table
ex:-->in the below customers is the right table
SELECT * FROM orders 
RIGHT JOIN customers
ON orders.cust_id=customers.cust_id;

cmd(ON DELETE CASCADE)-->
it is used in a foreign key constraint to automatically delete rows in a child table when the corresponding rows in the parent table are deleted.

CREATE TABLE orders(
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    date DATE DEFAULT CURRENT_TIMESTAMP,
    amount DECIMAL(10,2),
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customers(cust_id) ON DELETE CASCADE
);

ex:--> in the below case we are using the inner join with case in which we are also creating a new column of remark  on the basis of the values if ratings
select author_name,ratings,
CASE
    WHEN ratings>=3 THEN "Good"
    ELSE "Average" 
END as remark
from authors
inner join books
on books.au_id=authors.author_id

Many-Many relationship:-

ex:-->we created two tables one is for courses and other one is for students , then we created a third table called student_course which i used to join the other two;

CREATE TABLE students(
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_name VARCHAR(20)
);
CREATE TABLE courses(
    id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(20),
    fees INT
);
CREATE TABLE student_course(
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES students(id);
    FOREIGN KEY (course_id) REFERENCES courses(id);
);
Now for many to many we use the below relationship :-->
SELECT student_name , course_name FROM students
JOIN
 student_course ON student_course.student_id=students.id
JOIN
 courses ON student_course.course_id=courses.id;

 cmd(VIEW)-->
//a view is a virtual table that provides a way to represent the result of a SQL query as if it were a real table. Views allow you to encapsulate complex queries and make them easier to reuse and manage

ex:-View creates an extra table of the name inst_info which is the result of the below query


 CREATE VIEW inst_info AS
 SELECT student_name , course_name,fees FROM students
JOIN 
     student_course ON student_course.student_id=students.id
JOIN 
     courses ON student_course.course_id=courses.id;

cmd(HAVING CLAUSE)-->

in the below code we used HAVING in place of the WHERE , as we cannot use WHERE  with GROUP BY
ex:-
SELECT student_name , SUM(fees) FROM insta_info GROUP BY student_name HAVING SUM(fees)>10000

cmd(GROUP BY ROLL UP)
the roll us provides adds another row with the total sum of the fees coloumn , we can use rollup with count, sum ,avg
SELECT IFNULL(student_name,"TOTAL"), SUM(fees) FROM inst_info GROUP BY student_name WITH ROLLUP;

cmd(STORED ROUTINE)-->
An SQL statement or a set of SQL Statement that can be stored on a database server which can be called number of times
a stored routine is a set of SQL statements that can be stored in the database and executed as a unit. 
Types:
1)STORED Procedure-->it performs operations but do not return a value , it contains a series of SQL statements and procedural logic and used for performing actions like modification , transaction control, and executing sequences of statements
ex:->

<!-- we can drop if exist already -->
DROP PROCEDURE IF EXISTS p_name;

<!-- Temp changing delimiter -->
DELIMITER $$  //in this code we made $$ our delimeter in place of semicolon

CREATE PROCEDURE p_name() //p_name is the name of the procedure
BEGIN
    SELECT * FROM employees
    LIMIT 10;
END$$ //once we reach the END then the code will run as we have changed the delimeter to $$

<!-- Again changing delimeter -->
DELIMETER ; //we again changed the delimeter back to semicolon

we can run the stored_procedure by either using --> CALL pname() //pname is the name of the procedure

Argument passing in stored procedure:-->

ex:-->in the below exmample we have taken p_fname as the input
DELIMETER $$
CREATE PROCEDURE get_empid (IN p_fname VARCHAR(50) )
BEGIN
    SELECT emp_id FROM employees
    WHERE fname=p_fname;
END$$
DELIMETER ;
// WE can call the above db by " call get_empid("rohit") " 

Returning Output in a Variable in STORED PROCEDURE

EX:->in the below code we're returning the value in the form of variable "p_sum" , we wrote INTO which means the value of SUM(SALARY) is to be stored in p_sum;
DELIMETER $$
CREATE PROCEDURE get_sum(IN p_fname VARCHAR(50),OUT p_sum DECIMAL(10,2))
BEGIN
 SELECT SUM(Salary) INTO p_sum FROM employees
 WHERE fname=p_fname;
END$$
DELIMETER ;

//how to execute the above code
SET @emp_sum=0;//we created a variable named emp_sum, 
call get_sum("Rohit",@emp_sum);
SELECT @emp_sum;//display the emp_sum;

2)User defined Functions


ex:-->in the below code we're fetching the data of the user with the highest salary
to run the below code we'll write "SELECT db_name.get_sum() "
DELIMETER $$

CREATE FUNCTION get_sum(p_fname VARCHAR(50)) RETURNS VARCHAR(50)
DETERMINISTIC NO SQL READS SQL DATA
BEGIN 
    DECLARE v_max INT;
    DECLARE v_name VARCHAR(50);

    SELECT MAX(SALARY) INTO v_max FROM employees;
    SELECT fname INTO v_name FROM employees WHERE salary=v_max;

    return v_name;
END$$

DELIMETER ;

cmd(WINDOW functions)-->it is used to perform calculations across a set of rows related to the current row
defined by OVER() clause.

ex:-->
//it will give the sum of the salaries but it will return the number of times of each row ,
SELECT SUM(salary) OVER() AS sum_salary FROM employees;

//we can even give multiple data in OVER()
SELECT 
emp_id,
fname,
salary,
SUM(salary) OVER(ORDER BY emp_id) AS sum_salary 
FROM employees;

//we are trying to get the sum of each department 
SELECT 
emp_id,
fname,
salary,
SUM(salary) OVER(PARTITION BY dept) AS sum_salary 
FROM employees;


SELECT 
emp_id,
fname,
salary,
MAX(salary) OVER(PARTITION BY dept) AS sum_salary 
FROM employees;

other functions such as ---> ROW_NUMBER(),RANK(),DENSE_RANK(),LAG(),LEAD()


ex:-->in the below code we're are sorting the salry on the basis of row number  
SELECT
ROW_NUMBER()  OVER(ORDER BY salary) AS row_no,
emp_id,
fname,
salary,
FROM employees;

ex:-->we're ranking the data on the basis of salary
SELECT
emp_id,
fname,
salary,
RANK() OVER(ORDER BY salary) AS rank_sal,
FROM employees;


SELECT
emp_id,
fname,
salary,
DENSE_RANK() OVER(ORDER BY salary) AS rank_sal,
FROM employees;

ex:->lag_sal displays the the salary value present before the current salary value
SELECT
emp_id,
fname,
salary,
LAG(salary) OVER() AS lag_sal,
FROM employees;

ex:->lead_sal displays the the salary value present ahead the current salary value
SELECT
emp_id,
fname,
salary,
LEAD(salary) OVER() AS lead_sal,
FROM employees;

SELECT
emp_id,
fname,
salary,
salary - LAG(salary) OVER(order by salary desc) AS diff_sal,
FROM employees;

