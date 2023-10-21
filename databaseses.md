# Databases

Store data, Form relation or connections, filer data, search data, perform crud operations.

## What is a database

Data is facts and firgures about anything. 

Data is stored in entities.

A row in a relation/table is called an **instance**. The **attributes** of the entity become the columns. 

* Object Oriented database stores data in form of objects instead of tables.
* Graph databases store the data in the form of nodes realations are the edges
* Document databases store data as JSON objects

Can be on a dedicated machine or on the cloud. 

### How is data related?

Columns/Attributes is are Field

Each Row is an instance/record of the Databases entity.
Tabelle hat einen Primary Key der einzigartig ist. Damit können auch mehrere Instanzen ähnliche Daten haben und es kann immer eindeutig zugeordnet werden welcher record/instance gemeint ist. 

Table could look like this for an order

OrderID is the **primary key field**. I.e each instance has a different entry here. CustomerID is a **foreign key**. It is the **primary key** int the customer database and this creates a relation between the order and an instance of a customer. 

<table>
	<tr>
		<th>OrderID</th>
		<th>CustomerID</th>
		<th>OrderDate</th>
		<th>DeliveryDate</th>
	</tr>
	<tr>
		<td>01</td>
		<td>C1</td>
		<td>2022-03-03</td>
		<td>2022-03-11</td>
	</tr>
	<tr>
		<td>02</td>
		<td>C2</td>
		<td>2022-03-04</td>
		<td>2022-03-12</td>
	</tr>
	<tr>
		<td>03</td>
		<td>C3</td>
		<td>2022-03-02</td>
		<td>2022-03-10</td>
	</tr>
	<tr>
		<td>...</td>
		<td>...</td>
		<td>...</td>
		<td>...</td>
	</tr>
</table>

### Visualizing data

Data can be visualized with

* Bar charts - x and y axis (i.e. books sold each year)
* Bubble charts - Related data to the size of a bubble. Country size -> The bigger a country's population the bigger the bubble. 
* Line charts - Usually to predict trends. Series of points. I.e. history of price of something
* Pie charts - Display how various data makes up 100%. Type of sports students prefer in a class. 

Other chart types are *gantt, dual axis, heat maps and scatter plots*


## Types of databases
Realtional databases have limitations. Primarily for storing **structured data** in a tabular format. (SQL databases)


### NoSQL
NoSQL databases are more flixble for storing and scaling data and also makes it easier to store unstructured data.

* Document databases
* Key-value databases 
* Graph databases

### Big Data
Data that grows exponentially with time. Social media, shopping sites. 

Combination of structured, semi-structured and unstructured data. Provides insights. 

## Cloud databases

Lack of infrastructure, mainenance and storage costs

-> Dropbox and iCloud

### MORE

* [What Is a Database](https://www.oracle.com/uk/database/what-is-database/)
* [What Is a Relational Database](https://www.ibm.com/topics/relational-databases)

# SQL - Structured Query Language

**CRUD Operations** - Create, Read, Update, Delete

Standard language that can be used with all databases. Particularly useful with realtional databases.

* MySQL
* PostgreSQL
* Oracle
* Microsoft SQL Server

## Database Management System

Changes SQL instructions into a form that the underlying database can understand.

## SQL Subsets

* **DDL (Data Definition language)**

```
DDL Create - Used to create storage objects in a database like tables
DDL Alter - Modify structure of a table (i.e add a column)
DDL Drop - REmove object from database
```

* **DML (Data Manipulation language)**

```
DML Insert - Insert records of data into a database table
DML Update - Change data
DML Delete - Remove data
```

* **DQL (Data query language)**

```
SELECT - Retrieve data from one or multiple tables based on filter criteria
```

* **DCL (Data control anguage)**

```
Grant access priviliges to users
```

## Advantages of SQL

* User-friendly. Not much coding skill needed.
* Standard language. Can be used with all Relational Databases
* Portable. Can used on any hardware or platform.
* Create databases
* Insert, update and delete data
* Covers all areas of database management and administration
* Process large amounts of data efficiently

## SQL Syntax

``` sql
-- Create a new database
CREATE DATABASE database_name;

-- Select a database
USE database_name;

-- Add a table to the current database
CREATE TABLE table_name (column_name1 datatype(size), column_name2 datatype(size), ...);

-- Adds a row with the column_one being set to value1
INSERT INTO table_name 
	(column_one, column_two, column_three, ...) 
	VALUES (value1, value2, value3, ...);
	
INSERT INTO Customers (ContactName, Address, City, PostalCode, Country)
	VALUES ('Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');

-- Changes the date of birth only for the student with ID 02.
UPDATE Sudent SET date_of_birth = '2000-08-18' WHERE ID = 02;

-- Deletes the instance where the id is 3 (the entire row)
DELETE FROM Student WHERE ID = 03;

-- Gets name and last from the student with id 1
SELECT first_name, last_name FROM Student WHERE ID = 01;

-- Delete database or table inside database
DROP TABLE table_name;

-- Adds a column to the table.
ALTER TABLE table_name ADD (column_name datatype(size));

-- Add primary key to the table
ALTER TABLE table_name ADD primary key (column_name);

-- Remove column from table
ALTER TABLE table_name DROP COLUMN column_name;

-- Change text length
ALTER TABLE table_name MODIFY column_name VARCHAR(100);

-- Removae all records from a table but do not delete the table itself
TRUNCATE TABLE table_name;

-- Retrieve data from table
SELECT * FROM table_name;
SELECT col1, col2 FROM table_name;

-- Add record of data to table
INSERT INTO table_name (column1, column2, column3) 
	VALUES (value1, value2, value3);
	
INSERT INTO players(ID, name, age, start_date) 
	VALUES (1, "Yuval", 25, CURRENT_DATE()),
			(3, "Karl", 26, "2020-06-17");
	
-- Modify or update data
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;

-- DCL: DATA CONTROL LANGUAGE
-- Give a user permission to access and manipulate a database
GRANT

-- Remove permissions from user
REVOKE

-- Save all changes made to the database
COMMIT

-- Restore database to last commited state
ROLLBACK
```

[Introdcution to SQL](https://beginnersbook.com/2018/11/introduction-to-sql/)

## What are tables
Rows and columns. Multiple tables in a database called relations as they relate to one other. Table is also known as an entity. 

Each **column/field** has a **name** and a **data type**. The data type defines what data can be in a table column and tells SQL what to expect in each column.

Row is a record.

* String (CHAR, VARCHAR)
* Numeric (INT, TINYINT (max. 255), BIGINT, FLOAT, REAL)
* Date and Time (DATE, TIME, DATETIME)
* Binary (BINARY, VARBINARY)
* Misc (CLOB - Large block of Text, BLOB - Collection of Binary Data)

The **Schema** describes the structe: I.e. Name of the Table, its attributes, and their names and data types.

There is a column which holds a key called the primary key. It is unique for each row/instance/record so that it can be identified even if another row has the same other attributes. 

A **Foreign key** relates an instance/record/row in one table to another one in another table. For instance a car can have an owner. So the car has a **foreign key** that is the **primary key** of the Owner in the owner database.

### Logical Database structure
Displayed using the **Entity Relationship Diagram (ERD)**. Displays also how relationships are establishes. 

* **One-to-One realtionships:** A married couple. The husband is related to the wife and the wife is realted to the husband.
* **One-to-Many realtionships:** One User has many comments on a social media platform but each comment only has one user.
* **Many-to-Many:** A course at university has many students enrolled in it and each student is enrolled in multiple courses.

### Resources

* [Relational Database Structure](https://www.ibm.com/docs/en/control-desk/7.6.0?topic=design-relational-database-structure)
* [Database Design Basics](https://support.microsoft.com/en-us/office/database-design-basics-eb2159cf-1e30-401a-8084-bd4f9c9ca1f5)


## Data Types

### CHAR vs VARCHAR

* **CHAR** stores fixed length - CHAR(50) Stores up to 50 Characters. Even if entry is shorter the entry occupies 50 chars.
* **VARCHAR** stores variable length - VARCHAR(50) Stores only the input. If the input is less than 50 char then only the needed space is occupied. Needs one byte per character + 2 bytes for length


### Other String Types

* **TINYTEXT** for text less than 255
* **TEXT** for text less than 65k chars
* **MEDIUM** for text 16.7 million chars
* **LONGTEXT** up to 4Gb

### Default Values & Constraints

**NOT NULL** - Entries in this column must always contain a value.
**DEFAULT** - Default value if no value provided by input

``` sql
-- NOT NULL
CREATE TABLE Customer (customer_id int NOT NULL, csutomer_name varchar(255) NOT NULL);

-- DEFAULT VALUE if no data provided
CREATE TABLE Player (name varchar(50) NOT NULL, city varchar(50) DEFAULT "Barcelona");
```

### Arithmetic Operators

``` sql
SELECT salary - tax FROM employee;

SELECT * FROM employee WHERE salary >= 40500;

SELECT name FROM employee WHERE salary + allowance = 20499;

-- The operators are: =, != or <>, >, <, >=, <=
```

### Sorting and filtering

**ORDER BY** clause can be added to a **SELECT** statement.

``` sql
SELECT column1, column2, column3, ...
FROM table_name
ORDER BY column_name ASC/DESC;

SELECT column1, column2
FROM table_name
ORDER BY column1 ASC, column2 DESC;
```

**WHERE**

``` sql
SELECT *
FROM table_name
WHERE date_of_birth BETWEEN "2010-08-18" AND "2000-07-28"

-- % is the wildcard operator like * in unix commands
-- The _ is a wildcard for just one character
-- This gets all records whose faculty start with 'Sc'
SELECT *
FROM table_name
WHERE faculty LIKE "Sc%";

-- All records that have a country that is either USA or Germany
SELECT *
FROM table_name
WHERE country IN ("USA", "Germany")
```

Multiple conditions can be given with the **AND** or **OR** keyword

**SELECT DISTINCT**

This returns a column of countries but without any duplicates. If multiple students are from the same country the country will still only be returned once.

``` sql
SELECT DISTINCT country
FROM students;

-- If multiple students are from the same country and in the same faculty
-- this combination will still only be returned once
SELECT DISTINCT faculty, country
FROM students;
```

### RESOURCES

* [Numeric Data Types SQL](https://learnsql.com/blog/understanding-numerical-data-types-sql/)


### Database Schema

**Schema** Organization of information and it's relationships

* SQL Server - Collection of individual but related components.
* Postgre SQL - Namespace with named database objects
* Oracle - Single Schema for each user

SQL Server Schema made out of Schema objects (Tables, Column, Relationships, Datatypes and keys)

Software developers work with database schemas on a **logical/conceptual schema**. This is usually done with an **ERD (Entity Relationship Diagram)**. Details about the physical implementation are hidden. (How exactly storage access works). Shows how data is structured in terms of tables and how the attributes are linked together

**Internal/Physical Schema** describes how the data shall be physically stored.

**External or view schema** describes how a user would want to see it. Someone in the sales department would only need to see sales related parts of the database.

``` sql
CREATE TABLE Customer (
  customer_id INT,
  name VARCHAR(100),
  address VARCHAR(255),
  email VARCHAR(100),
  phone VARCHAR(10),
  PRIMARY KEY (customer_id)
);

CREATE TABLE Product (
  product_id INT,
  name VARCHAR(100),
  price NUMERIC(8, 2),
  description VARCHAR(255)
  PRIMARY KEY (product_id)
);

CREATE TABLE Cart_oder (
  order_id INT,
  customer_id INT,
  product_id INT,
  quantity INT,
  order_date DATE,
  status VARCHAR(100),
  PRIMARY KEY (order_id),
  FOREIGN KEY (customer_id) REFERENCES Customer(customer_id),
  FOREIGN KEY (product_id) REFERENCES Product(product_id)
);

```

## MORE ON SCHEMAS

* [What is a database schema](https://www.ibm.com/topics/database-schema)
* [What are database schemas](https://www.educative.io/blog/what-are-database-schemas-examples)
* [Introduction to database schemas](https://www.prisma.io/dataguide/intro/intro-to-schemas)
* [Entity Relationship Model](https://opentextbc.ca/dbdesign01/chapter/chapter-8-entity-relationship-model/)


## Database normalization

Some issues with databases (duplicated data, issues with updating data and effort to query) can be solved with database normalization.

* Insert anomaly - Insert only possible if all records are correct
* Update anomaly - If a record that is used in a foreign key elsewhere is update, that change must be reflected everywhere where this records has been referenced. Otherwise an incorrect entry is left over.
* Delete anomaly - Deleting an element causes other data to be deleted as well. If a record is delted that is referenced elsewhere then that data must also be deleted/updated. 

Normalization optimizes the database design by creating a single purpose for each table. 

### Unnormalized

<table>
	<tr>
		<th>Student ID</th>
		<th>Student Name</th>
		<th>Course Name</th>
		<th>Course Credit</th>
		<th>Department Name</th>
		<th>Department Director</th>
		<th>Department Tel No.</th>
	</tr>
	<tr>
		<td>01</td>
		<td>Anita</td>
		<td>Computer Science</td>
		<td>160</td>
		<td>Computing</td>
		<td>Dr. Jones</td>
		<td>+1 464-371</td>
	</tr>
	<tr>
		<td>02</td>
		<td>Pedro</td>
		<td>Computer Science</td>
		<td>160</td>
		<td>Computing</td>
		<td>Dr. Jones</td>
		<td>+1 464-371</td>
	</tr>
	<tr>
		<td>03</td>
		<td>Nick</td>
		<td>Ancient Civilizations</td>
		<td>80</td>
		<td>History</td>
		<td>Dr. Shalvey</td>
		<td>+1 464-371</td>
	</tr>
	<tr>
		<td>04</td>
		<td>Rose</td>
		<td>UX Design</td>
		<td>120</td>
		<td>Design</td>
		<td>Dr. Patel</td>
		<td>+1 464-381</td>
	</tr>
</table>

### Normalized
**Student Table**
<table>
	<tr>
		<th>Student ID</th>
		<th>Student Name</th>
		<th>Course ID</th>
	</tr>
	<tr>
		<td>01</td>
		<td>Anita</td>
		<td>01</td>
	</tr>
	<tr>
		<td>02</td>
		<td>Pedro</td>
		<td>01</td>
	</tr>
	<tr>
		<td>03</td>
		<td>Nick</td>
		<td>02</td>
	</tr>
	<tr>
		<td>04</td>
		<td>Rose</td>
		<td>03</td>
	</tr>
</table>

**Course Table**
<table>
	<tr>
		<th>Course ID</th>
		<th>Course Name</th>
		<th>Course Credit</th>
		<th>Department ID</th>
	</tr>
	<tr>
		<td>01</td>
		<td>Computer Science</td>
		<td>160</td>
		<td>01</td>
	</tr>
	<tr>
		<td>02</td>
		<td>Ancient Civilizations</td>
		<td>80</td>
		<td>02</td>
	</tr>
	<tr>
		<td>03</td>
		<td>UX Design</td>
		<td>120</td>
		<td>03</td>
	</tr>
</table>

**Department Table**
<table>
	<tr>
		<th>Department ID</th>
		<th>Department Name</th>
		<th>Department Director</th>
		<th>Department Tel No.</th>
	</tr>
	<tr>
		<td>01</td>
		<td>Computing</td>
		<td>Dr. Jones</td>
		<td>+1 464-371</td>
	</tr>
	<tr>
		<td>02</td>
		<td>History</td>
		<td>Dr. Shalvey</td>
		<td>+1 464-371</td>
	</tr>
	<tr>
		<td>03</td>
		<td>Design</td>
		<td>Dr. Patel</td>
		<td>+1 464-381</td>
	</tr>
</table>

### Normal Forms

* **First Normal Form (1NF)** - Atomicity Rule: Only ever one value per field. I.e not multiple phone numbers in a 'Tel No.' Field. Also avoid uneccessarys repetiton of groups of data. Like in the unnormalited exmaple above where in multiple rows the same department information was stored. Or the same infromation about courses was stored multiple times in multiple rows. Instead introduce a foregin key and refernce it.

* **Second Normal Form (2NF)** - Avoid Partial Dependency relationships between data. Only the case on tables with a *compsite primary key*. Partial dependency realtionships mean that a non-key attribute depends on only one part of the composite key. 

* **Third Normal Form (3NF)** - Must already be in 2NF and additionally have no *transitive depencency*. Two non-key attributes may not be functionally dependant. I.e. if you have a city and a postcode. If you change the city you also have to change the post code. That is not allowed in 3NF.


In this Table there still is a transitive dependency. The language can be used to determine the country and vice versa. So this should be resolved. 

**Tables with transitional dependency**
<table>
	<tr>
		<th>ID</th>
		<th>Author</th>
		<th>Language</th>
		<th>Country</th>
		<th>Book title</th>
	</tr>
	<tr>
		<td>1</td>
		<td>Marit Hagen</td>
		<td>Norwegian</td>
		<td>Norway</td>
		<td>Title 1</td>
	</tr>
	<tr>
		<td>2</td>
		<td>Michel Lloris</td>
		<td>French</td>
		<td>France</td>
		<td>Title 2</td>
	</tr>
	<tr>
		<td>3</td>
		<td>Cormac O'Dwyer</td>
		<td>Irish</td>
		<td>Ireland</td>
		<td>Title 3</td>
	</tr>
	<tr>
		<td>4</td>
		<td>Michel Lloris</td>
		<td>Spanish</td>
		<td>Spain</td>
		<td>Title 4</td>
	</tr>
	<tr>
		<td>5</td>
		<td>Lucas Pavard</td>
		<td>French</td>
		<td>France</td>
		<td>Title 5</td>
	</tr>
</table>

**Tables without transitional dependency**
<table>
	<tr>
		<th>ID</th>
		<th>Author</th>
		<th>Country</th>
		<th>Book title</th>
	</tr>
	<tr>
		<td>1</td>
		<td>Marit Hagen</td>
		<td>Norway</td>
		<td>Title 1</td>
	</tr>
	<tr>
		<td>2</td>
		<td>Michel Lloris</td>
		<td>France</td>
		<td>Title 2</td>
	</tr>
	<tr>
		<td>3</td>
		<td>Cormac O'Dwyer</td>
		<td>Ireland</td>
		<td>Title 3</td>
	</tr>
	<tr>
		<td>4</td>
		<td>Michel Lloris</td>
		<td>Spain</td>
		<td>Title 4</td>
	</tr>
	<tr>
		<td>5</td>
		<td>Lucas Pavard</td>
		<td>France</td>
		<td>Title 5</td>
	</tr>
</table>

<table>
	<tr>
		<th>Country</th>
		<th>Language</th>
	</tr>
	<tr>
		<td>Norway</td>
		<td>Norwegian</td>
	</tr>
	<tr>
		<td>France</td>
		<td>French</td>
	</tr>
	<tr>
		<td>Spain</td>
		<td>Spanish</td>
	</tr>
	<tr>
		<td>Ireland</td>
		<td>Irish</td>
	</tr>
</table>


# RESOURCES

* [Normalization](https://opentextbc.ca/dbdesign01/chapter/chapter-12-normalization/)
* [Normalization Step-By-Step](https://www.databasestar.com/database-normalization/)
* [DB Anomalies](https://www.bbc.co.uk/bitesize/guides/zc93tv4/revision/2)


MOd 3 Lesson 1 SQL Operators