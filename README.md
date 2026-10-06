# 📚 Smart Library Management System – SQL

## 📌 Project Overview

**Smart Library Management System** is a SQL-based database project designed to manage books, library members, borrowing transactions, and related library information.

The project demonstrates important SQL concepts through practical queries, including:

- SQL operators and filtering
- Sorting and grouping
- Aggregate functions
- Primary Key and Foreign Key relationships
- SQL JOINs
- Date and time functions
- String manipulation functions
- Window functions
- CASE expressions
- Practical library data analysis

---

## 🎯 Project Objectives

The main objectives of this project are:

1. Create and manage a relational library database.
2. Store information about books and library members.
3. Track book borrowing transactions.
4. Retrieve useful information using SQL queries.
5. Analyze library data using aggregate and window functions.
6. Understand relationships between database tables.
7. Practice real-world SQL data-analysis operations.

---

## 🗂️ Suggested Database Structure

The project can be organized around tables such as:

### 1. `Books`

Stores information about books.

| Column | Description |
|---|---|
| `BookID` | Unique ID of the book |
| `Title` | Book title |
| `Author` | Author name |
| `Category` | Book category |
| `Price` | Book price |
| `PublishedDate` | Publication date |
| `Availability` | Availability status |

### 2. `Members`

Stores library member information.

| Column | Description |
|---|---|
| `MemberID` | Unique member ID |
| `MemberName` | Member name |
| `JoinDate` | Membership date |

### 3. `Borrowings`

Stores book borrowing transactions.

| Column | Description |
|---|---|
| `BorrowID` | Unique borrowing ID |
| `BookID` | Borrowed book ID |
| `MemberID` | Member who borrowed the book |
| `BorrowDate` | Date on which the book was borrowed |
| `ReturnDate` | Date on which the book was returned |

> **Note:** Column names can be adjusted to match the actual SQL script used in the project.

---

## 🔑 Database Relationships

The project uses relational database concepts.

- `Books.BookID` → Primary Key
- `Members.MemberID` → Primary Key
- `Borrowings.BorrowID` → Primary Key
- `Borrowings.BookID` → Foreign Key referencing `Books`
- `Borrowings.MemberID` → Foreign Key referencing `Members`

These relationships connect books, members, and borrowing transactions.

---

# 🧪 SQL Tasks Covered

## 1. SQL Operators

The project uses operators such as:

- `AND`
- `OR`
- `NOT`
- `<>`
- `=`
- `<`
- `>`
- `<=`
- `>=`

### Example

```sql
SELECT *
FROM Books
WHERE Category = 'Science'
  AND Price < 500;
```

This retrieves Science books whose price is below 500.

---

## 2. Filtering Data

Filtering is used to retrieve records according to specific conditions.

Examples include:

- Books from a particular category
- Books below a particular price
- Unavailable books
- Members who borrowed books before a specific year
- Books borrowed more than three times

### Example

```sql
SELECT *
FROM Books
WHERE Availability = 'Not Available';
```

---

## 3. Sorting and Grouping

The project demonstrates:

- `ORDER BY`
- `GROUP BY`

### Sort books alphabetically

```sql
SELECT *
FROM Books
ORDER BY Title ASC;
```

### Group books by category

```sql
SELECT Category, COUNT(*) AS TotalBooks
FROM Books
GROUP BY Category;
```

---

## 4. Aggregate Functions

The project uses:

- `SUM()`
- `AVG()`
- `MAX()`
- `MIN()`
- `COUNT()`

### Example

```sql
SELECT
    COUNT(*) AS TotalBooks,
    AVG(Price) AS AveragePrice,
    MAX(Price) AS HighestPrice,
    MIN(Price) AS LowestPrice
FROM Books;
```

These functions help summarize library data.

---

## 5. Primary Key and Foreign Key

### Primary Key

A Primary Key uniquely identifies each record.

Example:

```sql
BookID INT PRIMARY KEY
```

### Foreign Key

A Foreign Key connects one table with another.

Example:

```sql
FOREIGN KEY (BookID) REFERENCES Books(BookID)
```

---

# 🔗 6. SQL JOINs

The project demonstrates different types of joins.

### INNER JOIN

Returns matching records from both tables.

```sql
SELECT b.Title, m.MemberName
FROM Borrowings br
INNER JOIN Books b
    ON br.BookID = b.BookID
INNER JOIN Members m
    ON br.MemberID = m.MemberID;
```

### LEFT JOIN

Returns all records from the left table and matching records from the right table.

### RIGHT JOIN

Returns all records from the right table and matching records from the left table.

### FULL OUTER JOIN

Returns matching and non-matching records from both tables where supported by the SQL database system.

---

# 📅 7. Date and Time Functions

Date functions are used to analyze borrowing and publication dates.

Examples:

- Extract year from a date
- Compare dates
- Find differences between dates
- Format dates

### Example

```sql
SELECT *
FROM Books
WHERE YEAR(PublishedDate) >= 2020;
```

Another practical use is calculating how long a book has been borrowed.

---

# 🔤 8. String Manipulation Functions

String functions are used to clean and transform text data.

Common functions include:

- `UPPER()`
- `LOWER()`
- `TRIM()`
- `CONCAT()`
- `REPLACE()`

### Example

```sql
SELECT UPPER(Title) AS BookTitle
FROM Books;
```

### Remove extra spaces

```sql
SELECT TRIM(Author) AS AuthorName
FROM Books;
```

---

# 📊 9. Window Functions

Window functions perform calculations across related rows without grouping the result into one row.

Examples:

- `ROW_NUMBER()`
- `RANK()`
- `DENSE_RANK()`
- Moving/average calculations

### Example

```sql
SELECT
    Title,
    Price,
    RANK() OVER (ORDER BY Price DESC) AS PriceRank
FROM Books;
```

This ranks books according to their price.

---

# 🧠 10. CASE Expressions

`CASE` is used to create conditional categories or labels.

### Example

```sql
SELECT
    Title,
    Price,
    CASE
        WHEN Price >= 500 THEN 'Expensive'
        WHEN Price >= 200 THEN 'Medium'
        ELSE 'Affordable'
    END AS PriceCategory
FROM Books;
```

This classifies books based on their price.

---

# 🔎 11. Example Analysis Queries

### Top 5 most expensive books

```sql
SELECT *
FROM Books
ORDER BY Price DESC
LIMIT 5;
```

### Science books below 500

```sql
SELECT *
FROM Books
WHERE Category = 'Science'
  AND Price < 500;
```

### Books borrowed more than 3 times

```sql
SELECT BookID, COUNT(*) AS BorrowCount
FROM Borrowings
GROUP BY BookID
HAVING COUNT(*) > 3;
```

---

# 🛠️ Tools & Technologies

- **SQL**
- Relational Database Management System (RDBMS)
- SQL Editor / Database Management Tool
- `library_management.sql`
- `README.md`

The exact SQL database system can be selected according to the course/project requirements.

---

# 📁 Project Structure

```text
Smart-Library-Management-System/
│
├── library_management.sql
└── README.md
```

### `library_management.sql`

Contains:

- Database/table creation
- Sample data
- Primary and foreign keys
- SQL queries
- Data analysis tasks

### `README.md`

Contains:

- Project description
- Objectives
- Database structure
- SQL concepts
- Examples
- Project instructions

---

# ▶️ How to Run the Project

## Step 1 — Open your SQL environment

Open MySQL, PostgreSQL, SQL Server, SQLite, or the database tool required by your course.

## Step 2 — Create the database

Create a database for the library project.

```sql
CREATE DATABASE LibraryManagement;
```

## Step 3 — Select the database

For MySQL:

```sql
USE LibraryManagement;
```

## Step 4 — Create the tables

Run the table-creation queries from:

```text
library_management.sql
```

## Step 5 — Insert the data

Run the sample `INSERT` statements.

## Step 6 — Execute the SQL queries

Run the project queries one by one and check the results.

---

# 📈 Expected Results

After completing the project, you should be able to:

- Find the most expensive books.
- Filter books using multiple conditions.
- Find unavailable books.
- Identify frequently borrowed books.
- Sort books and members.
- Group books by category.
- Calculate total, average, maximum and minimum values.
- Connect tables using JOINs.
- Analyze dates.
- Clean and transform text.
- Rank books using window functions.
- Categorize records using CASE expressions.

---

# 💡 Key SQL Concepts Learned

| Concept | Purpose |
|---|---|
| `SELECT` | Retrieve data |
| `WHERE` | Filter records |
| `AND / OR / NOT` | Combine conditions |
| `ORDER BY` | Sort records |
| `GROUP BY` | Create groups |
| `HAVING` | Filter groups |
| `SUM()` | Calculate total |
| `AVG()` | Calculate average |
| `MAX()` | Find maximum |
| `MIN()` | Find minimum |
| `COUNT()` | Count records |
| `PRIMARY KEY` | Uniquely identify records |
| `FOREIGN KEY` | Create table relationships |
| `JOIN` | Combine related tables |
| Date Functions | Work with dates |
| String Functions | Work with text |
| Window Functions | Perform row-based analysis |
| `CASE` | Apply conditions |

---

# 🎓 Learning Outcome

This project provides practical experience with SQL by applying database concepts to a real-world **library management system**.

After completing it, a student should have a better understanding of:

- Relational database design
- SQL querying
- Data filtering and sorting
- Data aggregation
- Table relationships
- JOIN operations
- Advanced SQL analysis
- Conditional data transformation

---

# 👩‍💻 Author

**Vaibhavi Sonigra**

**Project:** Smart Library Management System  
**Technology:** SQL  
**File:** `library_management.sql`

---

## ⭐ Conclusion

The **Smart Library Management System** is a practical SQL project that combines basic, intermediate, and advanced SQL concepts in one real-world application. It is useful for learning database management, SQL querying, and data analysis.

> **Practice SQL one query at a time — understand the logic, not just the syntax.**
