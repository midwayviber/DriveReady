# I. Introduction to SQL  

## Database  
**Definition:**  
A database is an organized collection of related data that can be accessed, managed, and updated efficiently.  

**Example:**  
A bank database storing customer details, account balances, and transactions.  

## Database Management System (DBMS)  
**Definition:**  
A DBMS is software that manages databases and provides an interface for users to store, retrieve, and manipulate data.  

**Examples:**  
- MySQL  
- PostgreSQL  
- Oracle Database  
- Microsoft SQL Server  

## Can a User Directly Interact with a Database?  
No, a user cannot directly interact with a database.  
To interact with a database, a user must use a software application like SQL.  

## Why Do We Use SQL?  
- To interact with and manage data stored in databases.  
- SQL allows users to insert, update, delete, and retrieve data efficiently.  
- It helps maintain data integrity and security.  
- It is used in almost all relational database management systems (RDBMS).  

## SQL (Structured Query Language)  
**Definition:**  
SQL is a standardized programming language used to manage and manipulate relational databases.  

**Features of SQL:**  
- Querying data (retrieving information)  
- Inserting and updating records  
- Deleting data  
- Creating and modifying database structures  
- Managing access control and security  

## Basic SQL Commands  

### Data Retrieval (SELECT)  
```sql
SELECT * FROM employees;
```
This retrieves all records from the "employees" table.  

### Insert Data (INSERT)  
```sql
INSERT INTO students (id, name, age) VALUES (1, 'John Doe', 20);
```
This adds a new student record into the "students" table.  

### Update Data (UPDATE)  
```sql
UPDATE students SET age = 21 WHERE id = 1;
```
This updates the age of the student with `id = 1`.  

### Delete Data (DELETE)  
```sql
DELETE FROM students WHERE id = 1;
```
This removes the student record with `id = 1`.  

## Conclusion  
- Databases store and manage data efficiently.  
- DBMS provides an interface to interact with databases.  
- SQL is the standard language used for managing relational databases.  
- SQL allows data retrieval, insertion, updating, and deletion.  

# II. **Types of Databases**  

Databases are mainly classified into **Relational** and **Non-Relational** databases.  

## **1. Relational Databases (RDBMS)**  
- **Definition:** Stores data in the form of structured tables with rows and columns.  
- **Follows ACID (Atomicity, Consistency, Isolation, Durability) properties** for data integrity.  
- **Uses SQL (Structured Query Language) for data management.**  
- **Examples:** MySQL, PostgreSQL, Oracle, Microsoft SQL Server.  

### **Table Example (Relational Database - MySQL)**  
| Student_ID | Name      | Age | Course  |  
|------------|----------|-----|--------|  
| 1          | John Doe | 20  | CS     |  
| 2          | Alice    | 22  | IT     |  

---

## **2. Non-Relational Databases (NoSQL)**  
- **Definition:** Does not store data in table format. Uses key-value, document, graph, or column-family models.  
- **Better for handling unstructured and semi-structured data.**  
- **Used for big data, real-time applications, and flexible schemas.**  
- **Examples:** MongoDB, Cassandra, Redis.  

### **Example (Non-Relational Database - MongoDB JSON Format)**  
```json
{
   "Student_ID": 1,
   "Name": "John Doe",
   "Age": 20,
   "Course": "CS"
}
```

---

## **Differences Between Relational and Non-Relational Databases**  

| Feature               | Relational Databases (SQL) | Non-Relational Databases (NoSQL) |  
|-----------------------|--------------------------|---------------------------------|  
| **Data Storage**      | Tables (Rows & Columns)  | Key-Value, Document, Graph, Column-Family |  
| **Schema**           | Fixed Schema (Predefined) | Flexible Schema (Dynamic) |  
| **Query Language**    | SQL                      | NoSQL Query (JSON, Key-Value, etc.) |  
| **Best For**         | Structured Data          | Unstructured & Semi-Structured Data |  
| **Examples**         | MySQL, PostgreSQL, Oracle | MongoDB, Redis, Cassandra |  

---

# **Data Types in SQL**  

SQL supports different **data types** to store various types of values.  

## **1. Numeric Data Types**  
Used for storing numbers.  

| Data Type | Description | Example |  
|-----------|------------|---------|  
| **INT**   | Stores whole numbers | `100, -50, 0` |  
| **FLOAT** | Stores decimal numbers (Less precise) | `12.34, -4.56` |  
| **DECIMAL(p, d)** | Stores exact decimal values | `DECIMAL(5,2) → 123.45` |  

**Precision in Decimal:**  
- **p (Precision):** Total number of digits.  
- **d (Scale):** Number of digits after the decimal point.  
- Example: `DECIMAL(5,2) → 123.45` (5 total digits, 2 after decimal).  

---

## **2. Character Data Types**  
Used for storing text and string values.  

| Data Type | Description | Example |  
|-----------|------------|---------|  
| **CHAR(n)** | Fixed-length string (Allocates full memory) | `CHAR(5) → "John " (Always 5 characters)` |  
| **VARCHAR(n)** | Variable-length string (Efficient memory usage) | `VARCHAR(5) → "John" (Uses only needed space)` |  

**Difference Between CHAR and VARCHAR:**  

| Feature  | CHAR | VARCHAR |  
|----------|------|---------|  
| **Length** | Fixed | Variable |  
| **Performance** | Faster for fixed-size data | More efficient for variable-length data |  
| **Example** | `CHAR(5) → "Hi   "` | `VARCHAR(5) → "Hi"` |  

---

## **3. Date and Time Data Types**  
Used to store date values.  

| Data Type | Description | Example |  
|-----------|------------|---------|  
| **DATE**  | Stores date in `YYYY-MM-DD` format | `2024-03-06` |  
| **TIME**  | Stores time in `HH:MI:SS` format | `12:30:45` |  
| **DATETIME** | Stores both date and time | `2024-03-06 12:30:45` |  

---

# **Summary Chart**  

```plaintext
   +------------------+--------------------+----------------+
   | Data Type       | Description        | Example        |
   +------------------+--------------------+----------------+
   | INT             | Whole numbers      | 100, -50       |
   | FLOAT           | Decimal numbers    | 12.34, -4.56   |
   | DECIMAL(p,d)    | Exact decimals     | 123.45        |
   | CHAR(n)         | Fixed-length text  | 'Hello '       |
   | VARCHAR(n)      | Variable text      | 'Hello'        |
   | DATE            | YYYY-MM-DD format  | 2024-03-06     |
   | TIME            | HH:MI:SS format    | 12:30:45       |
   | DATETIME        | Date + Time        | 2024-03-06 12:30:45 |
   +------------------+--------------------+----------------+
```

---

# **Conclusion**  
- **Relational Databases** store data in tables (MySQL, PostgreSQL).  
- **Non-Relational Databases** use flexible formats (MongoDB, Redis).  
- SQL supports **various data types** for handling numbers, text, and dates efficiently.


# **III. SQL Commands**  

## **I. DQL (Data Query Language)**  
Used to retrieve data from the database.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **SELECT** | Retrieves data from tables | `SELECT * FROM students;` |  

---

## **II. DML (Data Manipulation Language)**  
Used to modify and manage data within tables.  

| Command   | Description | Example |  
|-----------|------------|---------|  
| **INSERT** | Adds new records | `INSERT INTO students (id, name) VALUES (1, 'John');` |  
| **UPDATE** | Modifies existing records | `UPDATE students SET name = 'Alice' WHERE id = 1;` |  
| **DELETE** | Removes records | `DELETE FROM students WHERE id = 1;` |  

---

## **III. DDL (Data Definition Language)**  
Used to define and modify database structure.  

| Command   | Description | Example |  
|-----------|------------|---------|  
| **CREATE** | Creates new tables/databases | `CREATE TABLE students (id INT, name VARCHAR(50));` |  
| **ALTER** | Modifies existing tables | `ALTER TABLE students ADD COLUMN age INT;` |  
| **RENAME** | Renames a table | `RENAME TABLE students TO learners;` |  
| **DROP** | Deletes a table/database | `DROP TABLE students;` |  
| **TRUNCATE** | Deletes all data but keeps the table structure | `TRUNCATE TABLE students;` |  

---

## **IV. DCL (Data Control Language)**  
Used to manage user access and permissions.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **GRANT** | Provides access to users | `GRANT SELECT ON students TO user1;` |  
| **REVOKE** | Removes access from users | `REVOKE SELECT ON students FROM user1;` |  

---

## **V. TCL (Transaction Control Language)**  
Used to manage transactions in a database.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **COMMIT** | Saves all changes made in the transaction | `COMMIT;` |  
| **ROLLBACK** | Reverts changes if an error occurs | `ROLLBACK;` |  
| **SAVEPOINT** | Creates a checkpoint in a transaction | `SAVEPOINT sp1;` |  

---

# **Summary Table**  

| Type  | Full Form | Purpose | Commands |  
|-------|----------|---------|----------|  
| **DQL** | Data Query Language | Retrieves data | `SELECT` |  
| **DML** | Data Manipulation Language | Modifies data | `INSERT`, `UPDATE`, `DELETE` |  
| **DDL** | Data Definition Language | Defines structure | `CREATE`, `ALTER`, `RENAME`, `DROP`, `TRUNCATE` |  
| **DCL** | Data Control Language | Manages access | `GRANT`, `REVOKE` |  
| **TCL** | Transaction Control Language | Controls transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |  

---

# **Conclusion**  
- **DQL** is used for retrieving data.  
- **DML** is used for inserting, updating, and deleting records.  
- **DDL** is used for defining database structure.  
- **DCL** is used for managing user permissions.  
- **TCL** is used for handling database transactions.  


# **III. SQL Commands**  

## **1. DQL (Data Query Language)**  
Used to retrieve data from the database.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **SELECT** | Retrieves data from tables | `SELECT * FROM students;` |  

---

## **2. DML (Data Manipulation Language)**  
Used to modify and manage data within tables.  

| Command   | Description | Example |  
|-----------|------------|---------|  
| **INSERT** | Adds new records | `INSERT INTO students (id, name) VALUES (1, 'John');` |  
| **UPDATE** | Modifies existing records | `UPDATE students SET name = 'Alice' WHERE id = 1;` |  
| **DELETE** | Removes records | `DELETE FROM students WHERE id = 1;` |  

---

## **3. DDL (Data Definition Language)**  
Used to define and modify database structure.   

**C-A-R-D-T**

| Command   | Description | Example |  
|-----------|------------|---------|  
| **CREATE** | Creates new tables/databases | `CREATE TABLE students (id INT, name VARCHAR(50));` |  
| **ALTER** | Modifies existing tables | `ALTER TABLE students ADD COLUMN age INT;` |  
| **RENAME** | Renames a table | `RENAME TABLE students TO learners;` |  
| **DROP** | Deletes a table/database | `DROP TABLE students;` |  
| **TRUNCATE** | Deletes all data but keeps the table structure | `TRUNCATE TABLE students;` |  

---

## **4. DCL (Data Control Language)**  
Used to manage user access and permissions.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **GRANT** | Provides access to users | `GRANT SELECT ON students TO user1;` |  
| **REVOKE** | Removes access from users | `REVOKE SELECT ON students FROM user1;` |  

---

## **5. TCL (Transaction Control Language)**  
Used to manage transactions in a database.  

| Command  | Description | Example |  
|----------|------------|---------|  
| **COMMIT** | Saves all changes made in the transaction | `COMMIT;` |  
| **ROLLBACK** | Reverts changes if an error occurs | `ROLLBACK;` |  
| **SAVEPOINT** | Creates a checkpoint in a transaction | `SAVEPOINT sp1;` |  

---

# **Summary Table**  

| Type  | Full Form | Purpose | Commands |  
|-------|----------|---------|----------|  
| **DQL** | Data Query Language | Retrieves data | `SELECT` |  
| **DML** | Data Manipulation Language | Modifies data | `INSERT`, `UPDATE`, `DELETE` |  
| **DDL** | Data Definition Language | Defines structure | `CREATE`, `ALTER`, `RENAME`, `DROP`, `TRUNCATE` |  
| **DCL** | Data Control Language | Manages access | `GRANT`, `REVOKE` |  
| **TCL** | Transaction Control Language | Controls transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |  

---

# **Conclusion**  
- **DQL** is used for retrieving data.  
- **DML** is used for inserting, updating, and deleting records.  
- **DDL** is used for defining database structure.  
- **DCL** is used for managing user permissions.  
- **TCL** is used for handling database transactions.  


# **IV. How to Create a Table**  

## **1. CREATE Command**  
Used to create a new table in a database.  

### **Syntax:**  
```sql
CREATE TABLE table_name (
    column_name1 data_type constraints,
    column_name2 data_type constraints,
    column_name3 data_type constraints,
    ...
);

