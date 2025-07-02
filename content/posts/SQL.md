
+++
date = '2025-07-01'
title = 'SQL(MySQL)'
+++


# SQL (MySQL)

> "The goal of SQL is not to make simple things possible, but to make complex things manageable."

## What is SQL?

SQL stands for **Structured Query Language**.  
It is a language used to talk to databases. We use it to store, get, update, and delete data from databases.

### We use SQL to:
- Create databases and tables.
- Insert new data.
- Read data.
- Update existing data.
- Delete data.

It helps us manage and organize information in a structured way.

## Why Do We Use SQL?

We use SQL because:
- It is easy to learn and use.
- It works with large amounts of data.
- It helps in building apps and websites that use data.
- It provides data security and control.
- It is used in almost every modern database system.

## What is RDBMS?

**RDBMS** (Relational Database Management System) is the system or software that stores data in the form of tables (rows and columns).  
Each table contains related data. For example, a student table may have columns like Name, Age, and ID.

### Popular RDBMS examples include:
- MySQL
- Oracle
- MS SQL Server
- IBM DB2
- Microsoft Access

RDBMS is the base for using SQL.

## What is MySQL?

MySQL is a popular RDBMS that uses SQL to manage databases.
- SQL is the language (like English).
- MySQL is a tool that understands and runs that language.

MySQL allows you to create databases, store data, and manage it using SQL commands.

### MySQL supports all standard SQL commands like:
- `CREATE TABLE`
- `INSERT INTO`
- `SELECT`
- `UPDATE`
- `DELETE`

You will use these commands in MySQL to perform different tasks.

## Advantages of SQL

- Simple and readable.
- Widely used and supported.
- Fast for large amounts of data.
- Works with many different systems.
- Secure with user control features.

## Disadvantages of SQL

- Can be hard to learn advanced queries.
- Some systems use slightly different versions of SQL.
- Not ideal for working with unstructured data like images or videos.
- Needs optimization for complex tasks.

## Example: Working with MySQL

### Step 1: Install MySQL

We can install it manually or through the command line (terminal).

```bash
sudo apt update
sudo apt install mysql-server
```

### Step 2: Start MySQL

```bash
sudo service mysql start
```

### Step 3: Enter MySQL

```bash
sudo mysql
```

After this, the MySQL server becomes active and shows a welcome message.

### Step 4: Show All Databases

```sql
SHOW DATABASES;
```

This shows a list of all existing databases on your system.

### Step 5: Create a Database

```sql
CREATE DATABASE school;
USE school;
```

**Explanation**:
- `CREATE DATABASE`: Make a new container to store tables and data.
- `USE`: Select the database you want to work in.

### Step 6: Create a Table

```sql
CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  class VARCHAR(10)
);
```

**Explanation**:
- `id INT AUTO_INCREMENT PRIMARY KEY`: Unique ID that auto-increments.
- `name VARCHAR(100)`: Name column with up to 100 characters.
- `age INT`: Age column with integers.
- `class VARCHAR(10)`: Class column with up to 10 characters.

### Step 7: Insert Data

```sql
INSERT INTO students (name, age, class)
VALUES ('Ayesha', 14, '8A'),
       ('Ali', 15, '9B');
```

**Explanation**:
- Adds new data into the students table.

### Step 8: View Data

```sql
SELECT * FROM students;
```

**Explanation**:
- `SELECT * FROM students;`: Fetch all columns from the students table.

---

This example explains how different SQL tools are used to manage data using MySQL.

MySQL is one of the most popular tools for managing data. It helps websites, apps, and companies store, organize, and access their information quickly and safely.

Whether it's user accounts, product details, or blog posts, MySQL keeps everything in order behind the scenes.

It's free, reliable, and widely used, which makes it a favorite choice for developers and businesses of all sizes. From small blogs to giant websites like Facebook, MySQL helps power the digital world.

> "SQL is how we ask the questions, MySQL is how we keep the answers."

**THANK YOU!**