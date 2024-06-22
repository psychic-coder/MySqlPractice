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



