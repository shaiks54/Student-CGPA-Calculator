# Student CGPA Calculator

A Java Swing desktop application that lets a student log in with their roll
number and password, then automatically calculates and displays their SGPA
(per semester) and overall CGPA, based on marks stored in a MySQL database.

## Overview

- Student logs in using their roll number and password
- On successful login, their Name, Roll Number, Branch, and Section are
  fetched and displayed
- SGPA is calculated separately for Semester 1 and Semester 2 based on
  subject marks stored in the database
- Overall CGPA is calculated as the average of both semesters' SGPA
- A dropdown lets the user view either semester's SGPA individually

## Requirements

- Java JDK 8 or later
- MySQL Server
- MySQL Connector/J (JDBC driver) on the classpath

## Database Setup

Create a database named `project` with the following tables:

```sql
CREATE DATABASE project;
USE project;

CREATE TABLE student (
    Roll VARCHAR(20) PRIMARY KEY,
    Name VARCHAR(100),
    Branch VARCHAR(50),
    Section VARCHAR(10),
    password VARCHAR(50)
);

CREATE TABLE First_Sem (
    roll VARCHAR(20),
    C INT,
    BC INT
);

CREATE TABLE Sec_Sem (
    roll VARCHAR(20),
    Java INT,
    DBMS INT
);
```

Update the `DB_URL`, `DB_USER`, and `DB_PASSWORD` constants at the top of
`StudentCgpaCalculator.java` to match your local MySQL setup.

## Usage

1. Set up the MySQL database as described above
2. Add MySQL Connector/J to your classpath
3. Compile and run:
   ```bash
   javac -cp .:mysql-connector-j-<version>.jar StudentCgpaCalculator.java
   java -cp .:mysql-connector-j-<version>.jar StudentCgpaCalculator
   ```
4. Enter a student's roll number and password to view their details and CGPA

## Tech Stack

Java, Java Swing (GUI), JDBC, MySQL

## Notes

This project was built as an academic exercise to practice GUI development
(Swing), JDBC database connectivity, and basic conditional logic for
grade calculation. It's a learning project, not production software — for
example, the database password is stored in plain text in the source code
and SQL queries are built with string concatenation rather than
parameterized queries, both of which would need to be fixed before any
real-world use.
