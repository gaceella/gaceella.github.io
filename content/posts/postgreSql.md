
+++
date = '2025-06-29'
title = 'PostgreSQL'
+++


# PostgreSQL

> "PostgreSQL is the world's most advanced open source relational database—powerful, reliable, and packed with features for developers and enterprises alike."

---

## What is SQL?

SQL stands for **Structured Query Language**. It's a language used to communicate with databases.

With SQL, you can:

- Add data
- Read data
- Update data
- Delete data

## What is RDBMS?

RDBMS stands for **Relational Database Management System**. It is a type of database where:

- Data is stored in tables (like Excel sheets).
- Tables can be related to each other using keys (like a student ID).

**Examples of RDBMS:**

- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server

## What is PostgreSQL, and How is it Related to RDBMS?

PostgreSQL is a popular open source RDBMS. That means:

- It stores data in tables
- Supports SQL to manage data
- Follows the rules of a relational database

> There are many options for RDBMS but the best one is PostgreSQL. It is the most advanced and useful tool for data management.

## Advantages of PostgreSQL

Here are the main benefits:

- **Free and Open Source**: No cost to use
- **Very Powerful**: Handles complex queries and large data
- **Secure**: Built-in features to protect data
- **Extensible**: You can add custom features
- **Supports JSON and NoSQL**: Works with non-tabular data too
- **Cross-platform**: Works on Windows, Mac, Linux

## Disadvantages of PostgreSQL

### More Complex for Beginners:

- Many features can feel overwhelming for beginners.
- Compared to MySQL, it's a bit harder to set up and use for small/simple projects.

### Memory Usage:

- Uses more memory and system resources than lighter databases.
- Might be an issue on low-end servers or very small apps.

### Slower for Very Simple Reads:

- For small, read-heavy applications, PostgreSQL might be a bit slower than MySQL.
- It focuses more on accuracy and complex logic than pure speed.

## Why PostgreSQL is Better Than MySQL

### Advanced Features:

PostgreSQL supports:

- Window functions
- Common Table Expressions (CTEs)
- Full-text search
- Custom data types
- Stored procedures in multiple languages

### Better for Complex Applications:

PostgreSQL is often chosen for:

- Financial systems
- Geographic data (GIS)
- Scientific/analytics workloads
- Any app needing powerful, reliable queries

### JSON + Relational = Hybrid Power:

- PostgreSQL supports both SQL tables and JSON data (like NoSQL).
- You can do complex queries on JSON — something MySQL is weaker at.

## Why Is PostgreSQL More Popular Now?

- More startups and big companies want advanced features
- Developers need flexibility + reliability
- Tools, cloud services, and communities are now stronger than before

---

# Installation of PostgreSQL on Ubuntu 22.04

This guide walks you through the process of installing PostgreSQL on Ubuntu 22.04, creating a database, inserting data, and running SQL queries.

### STEP 1: Visit Official Website

- Open [PostgreSQL Official Website](https://www.postgresql.org/)
- Click **Download**
- Select **Linux** → **Ubuntu** (if you're using Ubuntu)

### STEP 2: Choose Linux Distribution

- Select **Ubuntu** under Linux distributions.

### STEP 3: Copy Installation Commands

- Follow commands exactly as shown on the site.

### STEP 4: Installing Required Dependencies

```bash
sudo apt install curl ca-certificates
```

**Output:**

```text
ca-certificates is already the newest version...
curl (7.81.0) will be installed...
```

### STEP 5: Import PostgreSQL Repository Key

```bash
sudo install -d /usr/share/postgresql-common/pgdg
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
```

### STEP 6: Add PostgreSQL APT Repository

```bash
. /etc/os-release
sudo sh -c "echo 'deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $VERSION_CODENAME-pgdg main' > /etc/apt/sources.list.d/pgdg.list"
```

### STEP 7: Update Package Lists

```bash
sudo apt update
```

### STEP 8: Install PostgreSQL 17

```bash
sudo apt -y install postgresql
```

### STEP 9: Accessing PostgreSQL

```bash
sudo -i -u postgres
psql
```

**Output:**

```text
psql (17.5)
Type "help" for help.
```

---

# Working with PostgreSQL

## STEP 1: Creating a Database

```sql
CREATE DATABASE school;
```

## STEP 2: Creating a Table

```sql
\c school
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name TEXT,
  class INT,
  roll_no INT
);
```

## STEP 3: Inserting Data

```sql
INSERT INTO students (name, class, roll_no) VALUES ('Khansa', 13, 19);
INSERT INTO students (name, class, roll_no) VALUES ('Momina', 1, 12);
```

## STEP 4: Retrieving Data

```sql
SELECT * FROM students;
```

## STEP 5: Updating Data

```sql
UPDATE students SET class = 2 WHERE name = 'Momina';
```

## STEP 6: View Updated Data

```sql
SELECT * FROM students;
```

## STEP 7: Delete Data

```sql
DELETE FROM students WHERE name = 'Khansa';
```

## STEP 8: View Final Data

```sql
SELECT * FROM students;
```

## STEP 9: Exit PostgreSQL

```sql
\q
```

---

# Installing pgAdmin 4 on Ubuntu

pgAdmin is a powerful GUI for PostgreSQL.

### STEP 1: Visit pgAdmin Website

- Click **Download**

### STEP 2: Select APT for Ubuntu

### STEP 3: Choose Ubuntu 22.04 (Jammy)

### STEP 4: Run the Script Commands

### STEP 5: Add pgAdmin Public Key & Repo

```bash
curl -fsS https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /usr/share/keyrings/packages-pgadmin-org.gpg
```

```bash
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```

### STEP 6: Install pgAdmin 4

```bash
sudo apt install pgadmin4
```

### STEP 7: Install Components Separately (Optional)

```bash
sudo apt install pgadmin4-desktop
sudo apt install pgadmin4-web
```

### STEP 8: Configure Web Mode

```bash
sudo /usr/pgadmin4/bin/setup-web.sh
```

### STEP 9: Access via Browser

```text
http://127.0.0.1/pgadmin4
```

### STEP 10 to STEP 28: Use pgAdmin Interface to Create Database/Table

```sql
CREATE TABLE public.students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    class INT,
    roll_no INT
);

INSERT INTO public.students (name, class, roll_no) VALUES
('Khansa', 13, 19),
('Momina', 1, 12);

SELECT * FROM public.students;
```

### STEP 30: Update Data

```sql
UPDATE public.students
SET class = 2
WHERE name = 'Momina';

SELECT * FROM public.students;
```

### STEP 31: Delete Data

```sql
DELETE FROM public.students
WHERE name = 'Khansa';
```

---

## Final Words

> "PostgreSQL isn't just a database; it's a foundation for building reliable, scalable, and intelligent applications—open to the world, yet strong at its core."

**Thank you!**

