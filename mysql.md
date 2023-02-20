# introduction

# SQL
- SQL stands for structured query language.
some of the important keywords, we must know in database
- **Data:** 
- Data refers to any collection of information, facts, or statistics that are stored, processed, or communicated for various purposes.
-  It can be in the form of numbers, text, images, audio, or video. Data is typically raw, unorganized, and lacks meaning or context until it is analyzed, interpreted, and transformed into useful information.

**database:** It is a collection of organized data that is stored electronically in a computer system. It is designed to store and manage large amount of structured data in a way that enables effecient retrieval, manipulation and analysis of information .

**Database Management System** is a software application that allows users to create, manage and manipulate databases. It provides an interface betweent the user and the database. enables the users to define ,create, modify and delete data in the database.
- The DBMS software handles tasks such as data organization, storage, retrieval, backup, security, and user management.
- It also allows multiple users to access and manipulate the database simultaneously while ensuring data integrity and consistency. Examples of popular DBMSs include MySQL, Oracle, Microsoft SQL Server, PostgreSQL, and MongoDB.

- There are several types of databases, each designed for specific purpose and usecase. Some of them are
<br>Relational databases<br>nosql database<br>graph database<br>graph based database<br>object oriented database<br>Timeseries database<br>spatial database<br>Hierarchial database

**RDBMS**:
- RDBMS stands for relational database management system
- It is a software system that defines relationship in the form of table of an objects.
- Table is a combination of rows and columns.
- Rows are also called as record/tuple
- columns are also called as attributes or tuple.
- the insertion of rows and columns is called cell.

![image](https://user-images.githubusercontent.com/89054489/219876382-adeb4142-d774-4fac-9db2-c232fef9dd8d.png)

The following are the some of the features of RDBMS :
- **Data integrity:** 
- Data integrity refers to the accuracy and consistency of data throughout its life cycle. In the context of databases.Data integrity is maintained by ensuring that the data stored in the database is accurate, complete and consistent.
- Data integrity is enforced by applying various constraints to the database schema such as primary keys, unique keys, foreign keys, check constraints and triggers. These constraints help to prevent the insertion of invalid or incosistent data into the databases.
- Data Integrity is used to restrict invalid data into the table. We can achive data integrity by
- data type
- constraints
-**Querylanguage:**
-**Scalability:**
-**AcidTransactions:**
- **Atomicity(A)** Refers to the property of a transaction where all the operations within a transaction are treated as single unit. If one operation fails then the entire transaction is rolled back to its previous state, and no changes are commited to the database. This ensures that the database remains in a consistent state.
-**Consistency:**consistency ensures that the trasaction brings the database from one valid state to another. In otherwords, the transaction should satisfy all the integrity constraints defined in the database schema. if any integrity constraint is violated during the transaction, the entire transaction is rolled back to its previous state and no changees are commited to the database.
-**Isolation:**It ensures that transactions are processed in parallel without interfering with eachother. Isolation ensures that transactions do not read or modify each other's data and that they are not affected by other transactions.
-**Durability:**It refers to the property of transaction where once a transaction is commited to the database, the changes made by the transaction are permanent and will survive any subsequent failures. This is usually achieved by writing the changes made by the transaction to a durable storage medium like hard disk.
- ACID transactions are essential for maintaining the integrity of the data stored in a database. They ensure that the data is processed in a reliable and predictable manner, and that  the database remains in a consistent state even in the presence of failures.
-**Security:**

**Datatypes:**
- Data type is a type of data, which we store in each columns of table here, we have three types of datatypes. They are
<br>a. Number<br>b. Char/varchar<br>c. Date<br>
**Number:** is a datatype where we input numeric values or data.<br>EX: Number(5)  --> -99999 to 99999
<br>Number(2)  --> -99 to 99
**char/varchar** Char /varchar datatype are used to store alphanumeric characters.
<br>EX: Char(5)  Max of 2000 characters
<br>varchar(5)   Max of 4000 characters
**Date:**-- Date datatype is used to store and enter valid date.<br>EX: dd/mm/yyyy or Mm/yyyy 
## MYSQL
- My sql is a popular, opensource Database<br>My sql databases are relational (Meaning data is stored inthe form of tables.)<br>It handles very large databases<br>It is very fast and reliable.<br>My sql is compatible with standard sql also.

**Constraints:**--Constraints are the conditions, which restrict the invalid data into the table and it is provided to the column of the tables.
--> Not null
--> Unique
--> primary key
--> Foreign key
--> Check

**a. Not null:**
**Null:** - Null means nothing
- Null is either zero nor a blank space
- Null never occupies space in the memory
- If we perform any arithmetic operation with null, results in null itself
- Two nulls are never same in oracle
- Null represents unknown value.
**Not null:** Not null is a constraint, where it will not accept duplicate values and it can accept multiple null values.
**b. Unique** Unique is constraint, where it will not accept duplicate values and it can accept multiple null values.
**c. primarykey** Primary key is a combination of not null and unique constaints. 
- primary key makes a column to uniquely identify rows of data.
- only one primary key is allowed in a table.
- creation of primary key is not mandatory but it is highly recommended.


**candidate Key** columns, which are eligible to become primary key are called as candidate key
**Alternate Key** Columns, which are eligible to become primary key but not chosen as primary key are called alternate key.

**Foreign keys:** Foreign key constraint is also called as referential integrating constraint.
- Foreign key creates relationship between two table(or two columns in a table)
- Foreign key created on the child table
- Foreign key can take both null and duplicate values.

- To create foreign key, the master / parent table should have a primary key column defined on the common column of the master table.

- We can have morethan one foreign key in a table.
**Check:**--Check is a constraint, which is used to provide additional validation as per the customer requirement specification.
<br>EX: Check(salary>0)

**SQL Statements:**
- DQL : Data query language
- DDL : Data definition language
- DML : Data manipulation language
- TCL : Transaction control language
- DCL : Data control language

**DQL**

SELECT    : It is used to retrieve the data from the database.

**DDL**

create : it is used to create a new table<br>
Alter : It is used to modify the structure of the table<br>
Rename : It is used to rename the table<br>
Truncate : It is a sql command that removes all rows from a table without deleting the table structure or any associated objects like indexes, constraints or triggers. in short, it resets the table to its original state, with no data in it. it can't be undone. as it permanently deletes all data in the table. `$ truncate table <tablename>;`<br>
Drop : It is a sql command that deletes an entire table, including its structure and all associated objects like indexes, constraints or triggers. This operation is irreversible and permanently deletes the table and its data from the database. `$ DROP table <tablename>;`<br>
**DML** :

Insert : It is used to insert records into the table<br>
Update : it is used to modify records in the table<br>
Delete : It is used to delete the records from the table<br>

**TCL**

commit : It is used to save DML changes
Rollback : it is used to restore earlier values
savepoint : It is used to save the statement names

**DCL**

Grant : It is used to give permission to access or privilege to user<br>
Revoke : It is used to take back the permission given to the user.


**commands:**

>`$ show user `-- command to display the current user<br>
`$ clear screen/cl scr `--clear the screen<br>
`$ exit`-- exit the application<br>
`$ select * from tab;`--To display list of tables, which are present in the current user<br>
`$ Describe EMP/ desc emp;`-- used to give details about employee table<br>
`$ show line size/page size `--to show the line size/page size<br>
`$ set line size/page size `--to set the line size/page size<br>
`$ select * from table;` -- To show the complete table specified.

**Projection:**: It is the process of selecting and retrieving specific columns from a table. when performing a projection, only the specific columns are returned in the result set, which can make the query more effecient by reducing the amount of data that needs to be processed.
syntax : `select column1, column2 from <table-name>;`<br>
**Distinct:** It is a keyword used in sql query to remove duplicates from the result set. when a query uses distinct, only one instance of each distinct value in the specified columns is returned in the result set.In short, It will be used to display only the unique values from the column of the table.syntax:`select distinct column_name from table_name`<br>
**expression** It is a combination of one or more values, operators, and SQL functions that can be evaluated to produce a  single value. Expressions are often used in sql queries to perform calculations or to manipulate data before it is returned in the result set. Expressions can include mathematical operations, string operations, and logical operations as well as functions like SUM, AVG, and MAX
syntax : `SELECT column1 + column2 AS sum FROM table_name;`

**Dual:** It is a dummy table used for independent calculation or operation<br>
**Alias:**It is the alternative name given to the column heading. 
- Alias name should mention next to the column name.Between column name and alias name, we can use 'as' keyword but not mandatory. 
- alias should enclosed by double quotes, if it is having special characters.
- underscore can be considered as character in alias rather than as special character.<br>
EX: select ename employee name from emp;  Incorrect<br>
select ename employee_name from emp;     correct <br>
select ename "employee name" from emp;   correct <br>

**literals:** literals can be number / character/ data.
- literals are all case sensitive
- if literals is a number, then no need to enclosing that within the single quotes
- if the literals are character /date, then it should be enclosed by single quotes.

**concatenation:** it is used to join two strings of data.
- concatenation represented in two vertical bars (||)

**edit command:** Edit command is used to modify the previous query.<br>'ED' can also be used instead of 'EDIT'.

// write a query to display employee name, salary, annual salary of all the employees.

`$ select ename, sal, sal*12 annual_sal from emp;`

list command -- list is used to display the previously executed sql statements.`$ list`
<br>
save command: -- It is used to save the previously executed query.<br>
Replace command : Replace is used to overwrite the existing document.<br>
append command : It is used to append/fetch the saved one.
<br>spooling: spooling is the process of saving the output of sql query to a file, usually for further processing or analysis. when you spool the output of a query, the result set is written to a file in a specific format that can be easily read and processed by other programs.<br>

`$ SQL> SPOOL output.txt<br>SQL> SELECT * FROM employees;<br>SQL> SPOOL OFF`

**sql * plus**: sql * plus is client tool installed along with database.<br>It has specific set of commands<br>It acts as an inteface between user and database.

Differences between SQL and SQL * plus
||SQL | SQL * PLUS |
|-----|-----|----|
|1| SQL is standard language to communicate with the database| SQL * plus is an environment, which supports write and execute queries |
|2|SQL is ANSIC standard | It belongs to oracle proprietary (tool developed by oracle) |
|3| In SQL, semicolon; is mandatory| In SQL * plus semicolon(;) is not mandatory |
|4|SQL commands cannot be abbreviated <br>Ex: select<br>create<br>update<br>delete| sql * plus commands can be abbreviated<br>EX: cl scr(clear screen)<br>ed (edit)etc|
|SQL commands can manipulate tables and data definitions| we cannot manipulate tables and definitions |

**operators**-- operators are the symbols used to perform some specific operations.<br>operands: these are the inputs required for the operations<br>
**Types of operators:**

-> Arithmetic operators (+,-,*,/,----)<br>
-> Comparision or Relational operators(>,<,>=,<=,!=,-->)<br>
-> logical operator (AND, OR, NOT)<br>
-> special operators (is, like, in ,between, having ----)

`$ Select * / {[distinct]Expression /column_name [alias]}<br>From <table_name><br>Where <condition/s>;`

--> select * from emp;
// write a query to display list of all employees, where salary is greater than 1000

` $ select * from emp where sal>2000;` 

// write a query to list all the details of employees, who are working as manager

`$ selct * from emp where job='MANAGER';`

// write a query to display all the employees, who are working in the department 20 and working as salesman

`$ select * from emp where deptno=20 and job='SALESMAN`

//write a query to display all the list of employees, who are working as manager and salary > 2000 and works in the department 30.

`$ select * from emp where job='MANAGER' and sal>2000 and deptno = 30;`

// write a query to display salary of scott.
`$ select SAL from emp where ename='scott'`;

// write a query to display the list of employee, who are working in the department 10,20 & 30.

`$ select * from emp where deptno=10 or deptno=20 or deptno=30;`

// write a query to display the list of employees who are working as clerk or salesman or analyst

`$ select * from emp where job='CLERK' or job='MANAGER' or job = 'ANALYST';`

**IN operator:** Instead of using multiple 'or' operators, we are using IN operator.
syntax: `$ select <column-list> from <table_name> where column_name in (v1,v2,v3,---); 

// write a query to display the list of employees, who are working as clerk, salesman and analyst

`$ select * from emp where job in ('CLERK', 'SALESMAN','ANALYST');`

// write a query to display the list of employees, who are working in department 10 and 20 and earning more than 500.

`$ select * from emp where deptno in (10,20) and sal>500;`

// write a query to display the list of employees, who are working as clerk & salesman in department 20 and 30, whose salaries should be greater than 1500.

`$ select * from emp where job in ('CLERK','SALESMAN') and deptno in (20,30) and sal>1500;`

// write a query to display list of employees, who are not working in department 20 & 30.

`$ select * from emp where deptno not in (20,30);`




## why are we using MYSQL ?
- free and opensource
- Easy to install, configure , fast performance with reliability
- Multiuser access to a number of databases offered
- Commercial version of MYSQL is also available

## History of MYSQL
-  founded and developed by David Axmark, Allan Larsson, and Micheal Monty Widenius
- Named after Monty's daughter named my
- My sql dolphin logo is "sakila" the name of a town in Arusha, Tanzania
- written in c and c++
- works on many different platforms
- sun acquired MYSQL AB in jan 2008 for $1 billion dollars

## MySql products

#### MY SQL server:
 - community server<br>Enterprise server<br>Embedded server<br>Cluster(standard and carrier-grade)

#### MySql GUI Tools
- Query Browser<br>Administrator<br>Migration Toolkit<br>Visual studio plugin<br>Mysql workbench

#### Mysql Drivers
- JDBC<br>ODBC<br>.NET<br>PHP

##### mysql server works in :
- **client/server system**-->a system that consists of a multithreaded sql server that supports different backends, several different client programs and libraries, administrative tools, and a wide range of applicaiton programming interfaces(API)<br>
**Embedded systems**-->provide mysql server as an embedded multi threaded library that can be linked into an application to get a smaller faster, easier-to-manage standalone product.

### MySql Features and benefits

|Feature  | Benefits |
|----------|---------|
|**scalability and flexibility**|Run anything from <br>deeply embedded applications with a footprint of just 1 MB or <br> Massive data warehouses holding terabytes of information|
|**High performance**|Table and index partitioning<br>ultra fast load utilities<br>Distinctive memory caches<br>fulltext indexes,and more|
|**High Availability**|Run highspeed  master/slave replication, configuration with Rowbased and hybrid replication<br>specialized cluster servers offering instant failover|
|**Robust Transactional support**|complete ACID(atomic, consistent, isolated, durable) transaction support<br> unlimited row level locking<br> distributed transaction capability and <br>multiversion transaction support<br>|
|**web and data warehouse strenghts**|High performance query engine<br>Tremendously fast data insertcapability<br>strong support for specialized web functions,like fast full text searches|
|**Strong data protection**|powerful mechanisms for ensuring only authorized users have access<br>SSH and SSL support safe and secure connections<br>powerful data encryption and decryption functions|
|**Comprehensive application development**|support stored procedures, triggers,functions, views, cursors, ANSI-standard SQL and more<br>plugin libraries to embed MYSQL database support into nearly any application|
|**Management Ease**|Use event scheduler automatically schedule common recurring sql based tasks to execute on the database server<br>average time from software download to complete installation is lessthan fifteen minutes|
|**opensource freedom and 24*7 support**|Around the clock support and indemnification available through mysql network<br> enterprise quality and enterprise ready from installation to support.|
|**Lowest Total cost of ownership**|save on database licensing costs and hardware expenditures, all while cutting systems downtime|

![image](https://user-images.githubusercontent.com/89054489/219843302-33c117a3-7934-4bda-91cc-46d35cf37fc6.png)

## mysql installation
##### Resources:
- General starting point `http://www.mysql.com`<br> Developer focussed `http://dev.mysql.com` and for installation `https://dev.mysql.com/doc/refman/5.7/en/installing.html`

### connecting and disconnecting to/from mysql

- commands meant to be executed from within a particular , for example `shell>``root-shell` is simmilar but should be executed as root
- `mysql>` indicates a statement that has to be executed from mysql client program.
- sql keywords are not casesensitive

**connecting to mysql:**
- mysql provides an interactive shell for creating tables, inserting data ,etc.
- on windows, just go to c:\mysql\bin, and type
`mysql` or `mysql-u user -p`
- To exit the mysql , type QUIT OR EXIT OR \q

