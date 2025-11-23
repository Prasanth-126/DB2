

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

