

# 📘 DB2 Database 

## 🗂️ What is DB2?
- **Developer:** IBM  
- **Type:** Relational Database Management System (RDBMS)  
- **Purpose:** Store, analyze, and retrieve data efficiently using SQL.  
- **Platforms:** Runs on **Linux, UNIX, Windows (LUW)**, and IBM mainframes.  

---

## ⚙️ Key Features
- **SQL Support** for querying and managing data.  
- **PureXML**: Native XML storage and querying.  
- **BLU Acceleration**: Columnar storage + in-memory analytics for faster performance.  
- **Cross-Platform**: Works across multiple operating systems.  
- **Scalability**: Handles large datasets and high transaction volumes.  

---

## 📜 Brief History
- Originated on IBM mainframes (1983).  
- Expanded in the 1990s as **DB2 Universal Database (UDB)**.  
- Versions evolved with codenames (*Stinger*, *Viper*, *Cobra*, *Kepler*).  
- Added features like PureScale clustering and advanced analytics.  

---


## 🏢 DB2 Use Cases
- **Banking & Finance:** High-volume transaction processing.  
- **Retail & Supply Chain:** Inventory and customer data management.  
- **Healthcare:** Secure patient record storage.  
- **Analytics:** Fast querying of large datasets.  

---

## ⚖️ DB2 vs Oracle vs MySQL

| Feature | **IBM DB2** | **Oracle Database** | **MySQL** |
|---------|-------------|----------------------|-----------|
| **Developer** | IBM | Oracle Corporation | Oracle Corporation |
| **Release Year** | 1983 | 1979 | 1995 |
| **Licensing** | Proprietary (with some free editions) | Proprietary | Open-source (GPL), with enterprise editions |
| **Strengths** | PureXML, BLU Acceleration, IBM integration | Mature, feature-rich, widely adopted | Lightweight, free, popular for web apps |
| **Performance** | Optimized for analytics & transactions | High performance for OLTP & OLAP | Good for small/medium workloads |
| **Scalability** | Enterprise-grade | Highly scalable | Limited for massive enterprise workloads |
| **Use Cases** | Banking, healthcare, analytics | Telecom, ERP, government | Websites, blogs, SaaS apps |

---

## 🗂️ DB2 Queries – Using AND
### Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3;
```

### Example 1
```sql
SELECT NAME, DEPARTMENT, SALARY
FROM EMPLOYEES
WHERE DEPARTMENT = 'IT' AND SALARY > 50000;
```
✅ Employees in IT **AND** salary above 50,000.

### Example 2
```sql
SELECT NAME, DEPARTMENT, SALARY
FROM EMPLOYEES
WHERE DEPARTMENT = 'HR' AND SALARY BETWEEN 30000 AND 60000 AND NAME LIKE 'A%';
```
✅ HR employees with salary between 30k–60k and names starting with "A".

### Example 3 (AND + OR)
```sql
SELECT NAME, DEPARTMENT, SALARY
FROM EMPLOYEES
WHERE (DEPARTMENT = 'Finance' AND SALARY > 70000)
   OR (DEPARTMENT = 'IT' AND SALARY > 60000);
```
✅ Finance employees >70k OR IT employees >60k.

---

## 🔑 Syntax Differences: DB2 vs MySQL

| Feature | **DB2** | **MySQL** |
|---------|---------|-----------|
| **String Concatenation** | `||` operator | `CONCAT()` function |
| **Limiting Rows** | `FETCH FIRST n ROWS ONLY` | `LIMIT n` |
| **Date/Time Functions** | `CURRENT DATE`, `CURRENT TIME` | `NOW()`, `CURDATE()` |
| **Boolean Values** | No native Boolean (uses `CHAR(1)`/`SMALLINT`) | `BOOLEAN` (alias for `TINYINT(1)`) |
| **Stored Procedures** | `BEGIN ATOMIC ... END` | `BEGIN ... END` |
| **Case Sensitivity** | Case-sensitive unless quoted | Case-insensitive (depends on OS) |
| **Auto Increment** | `GENERATED ALWAYS AS IDENTITY` | `AUTO_INCREMENT` |

### Example Comparison
**DB2:**
```sql
SELECT NAME, DEPARTMENT
FROM EMPLOYEES
FETCH FIRST 5 ROWS ONLY;
```

**MySQL:**
```sql
SELECT NAME, DEPARTMENT
FROM EMPLOYEES
LIMIT 5;
```

---

# ✅ Summary
- **DB2**: IBM’s enterprise-grade RDBMS with advanced analytics and XML support.  
- **Enterprises**: Large organizations needing scalable, reliable solutions.  
- **Queries**: AND operator filters rows by multiple conditions.  
- **Differences**: DB2 is stricter and ANSI-compliant, while MySQL is flexible and open-source.  
- **Comparison**: DB2 excels in enterprise analytics, Oracle dominates mission-critical systems, MySQL thrives in web apps.  


# 🗂️ DB2 CRUD Operations

## 1️⃣ CREATE (Insert Data)
Used to add new records into a table.

```sql
-- Create a sample table
CREATE TABLE EMPLOYEES (
    EMP_ID INT GENERATED ALWAYS AS IDENTITY,
    NAME VARCHAR(50),
    DEPARTMENT VARCHAR(30),
    SALARY DECIMAL(10,2)
);

-- Insert a single record
INSERT INTO EMPLOYEES (NAME, DEPARTMENT, SALARY)
VALUES ('John Doe', 'IT', 60000);

-- Insert multiple records
INSERT INTO EMPLOYEES (NAME, DEPARTMENT, SALARY)
VALUES 
('Alice', 'HR', 45000),
('Bob', 'Finance', 70000);
```

---

## 2️⃣ READ (Select Data)
Used to retrieve records from a table.

```sql
-- Select all records
SELECT * FROM EMPLOYEES;

-- Select specific columns
SELECT NAME, SALARY FROM EMPLOYEES;

-- Select with condition
SELECT NAME, DEPARTMENT, SALARY
FROM EMPLOYEES
WHERE DEPARTMENT = 'IT' AND SALARY > 50000;

-- Limit rows (DB2 syntax)
SELECT NAME, DEPARTMENT
FROM EMPLOYEES
FETCH FIRST 5 ROWS ONLY;
```

---

## 3️⃣ UPDATE (Modify Data)
Used to change existing records.

```sql
-- Update salary of a specific employee
UPDATE EMPLOYEES
SET SALARY = 65000
WHERE NAME = 'John Doe';

-- Update multiple columns
UPDATE EMPLOYEES
SET SALARY = SALARY + 5000, DEPARTMENT = 'Operations'
WHERE DEPARTMENT = 'HR';
```

---

## 4️⃣ DELETE (Remove Data)
Used to delete records from a table.

```sql
-- Delete a specific record
DELETE FROM EMPLOYEES
WHERE NAME = 'Bob';

-- Delete all records in a department
DELETE FROM EMPLOYEES
WHERE DEPARTMENT = 'Finance';

-- Delete all records (truncate-like)
DELETE FROM EMPLOYEES;
```

---

# ✅ Summary
- **CREATE → INSERT** new records.  
- **READ → SELECT** records with conditions.  
- **UPDATE → MODIFY** existing records.  
- **DELETE → REMOVE** records.  


# ✅ Key Differences
**Auto Increment :**
- DB2 → GENERATED ALWAYS AS IDENTITY
- MySQL → AUTO_INCREMENT
- Oracle → GENERATED ALWAYS AS IDENTITY (modern versions)
  
**Limit Rows:**
- DB2 → FETCH FIRST n ROWS ONLY
- MySQL → LIMIT n
- Oracle → FETCH FIRST n ROWS ONLY (older versions used ROWNUM)
  
**Data Types:**
- DB2 → VARCHAR, DECIMAL
- MySQL → VARCHAR, DECIMAL
- Oracle → VARCHAR2, NUMBER



# 🔗 SQL JOIN Syntax

## 1️⃣ INNER JOIN
Returns rows when there is a match in both tables.  

```sql
SELECT E.NAME, D.DEPARTMENT_NAME
FROM EMPLOYEES E
INNER JOIN DEPARTMENTS D
ON E.DEPARTMENT_ID = D.DEPARTMENT_ID;
```

✅ Only employees with a matching department are returned.  

---

## 2️⃣ LEFT JOIN (LEFT OUTER JOIN)
Returns all rows from the **left table** and matched rows from the right table.  

```sql
SELECT E.NAME, D.DEPARTMENT_NAME
FROM EMPLOYEES E
LEFT JOIN DEPARTMENTS D
ON E.DEPARTMENT_ID = D.DEPARTMENT_ID;
```

✅ Employees are shown even if they don’t belong to a department (NULL for missing matches).  

---

## 3️⃣ RIGHT JOIN (RIGHT OUTER JOIN)
Returns all rows from the **right table** and matched rows from the left table.  

```sql
SELECT E.NAME, D.DEPARTMENT_NAME
FROM EMPLOYEES E
RIGHT JOIN DEPARTMENTS D
ON E.DEPARTMENT_ID = D.DEPARTMENT_ID;
```

✅ All departments are shown, even if no employees are assigned.  

---

## 4️⃣ FULL JOIN (FULL OUTER JOIN)
Returns rows when there is a match in **either table**.  

```sql
SELECT E.NAME, D.DEPARTMENT_NAME
FROM EMPLOYEES E
FULL JOIN DEPARTMENTS D
ON E.DEPARTMENT_ID = D.DEPARTMENT_ID;
```

✅ Shows all employees and all departments, with NULLs where no match exists.  
- **DB2 & Oracle** support `FULL JOIN`.  
- **MySQL** does not support it directly (workaround: `UNION` of LEFT + RIGHT joins).  

---

## 5️⃣ CROSS JOIN
Returns the **Cartesian product** (all combinations of rows).  

```sql
SELECT E.NAME, D.DEPARTMENT_NAME
FROM EMPLOYEES E
CROSS JOIN DEPARTMENTS D;
```

✅ If 10 employees and 5 departments → 50 rows returned.  

---

## 6️⃣ SELF JOIN
A table joins with itself.  

```sql
SELECT E1.NAME AS EMPLOYEE, E2.NAME AS MANAGER
FROM EMPLOYEES E1
INNER JOIN EMPLOYEES E2
ON E1.MANAGER_ID = E2.EMP_ID;
```

✅ Useful for hierarchical data (employees and their managers).  

---

# ✅ Summary
- **INNER JOIN** → Only matching rows.  
- **LEFT JOIN** → All left + matches.  
- **RIGHT JOIN** → All right + matches.  
- **FULL JOIN** → All rows from both sides.  
- **CROSS JOIN** → Cartesian product.  
- **SELF JOIN** → Join table with itself.  



--
