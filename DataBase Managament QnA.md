

---

### **1. What is DBMS?**

* **DBMS (Database Management System)** manages data efficiently and allows multiple users to access it safely.
* Examples: MySQL, Oracle, PostgreSQL.

---

### **2. What is the difference between DBMS and RDBMS?**

| Feature   | DBMS             | RDBMS                      |
| --------- | ---------------- | -------------------------- |
| Structure | Data in files    | Data in tables (relations) |
| Keys      | No relationships | Primary & foreign keys     |
| Example   | MS Access        | MySQL, Oracle              |

---

### **3. What are the advantages of DBMS?**

* Data consistency & integrity
* Reduced redundancy
* Concurrent access control
* Data security & backup support

---

### **4. What is normalization?**

* Process of organizing data to reduce redundancy and improve integrity.
* Normal forms: 1NF → 2NF → 3NF → BCNF.
* Example: Split large table into smaller, related ones.

---

### **5. What is a primary key, foreign key, and unique key?**

* **Primary Key:** Uniquely identifies a record; no NULLs.
* **Foreign Key:** References primary key in another table.
* **Unique Key:** Ensures uniqueness but allows one NULL.

---

### **6. What are joins? Name types of joins.**

* Combines rows from two or more tables based on a related column.
* Types: INNER, LEFT, RIGHT, FULL, SELF, CROSS.

---

### **7. What are ACID properties?**

* **A**tomicity: All or none.
* **C**onsistency: Database remains valid.
* **I**solation: Transactions don’t interfere.
* **D**urability: Changes persist after commit.

---

### **8. What is the difference between DELETE, TRUNCATE, and DROP?**

| Command  | Removes       | Rollback | Affects Structure |
| -------- | ------------- | -------- | ----------------- |
| DELETE   | Specific rows | Yes      | No                |
| TRUNCATE | All rows      | No       | No                |
| DROP     | Entire table  | No       | Yes               |

---

### **9. What is a transaction?**

* A logical unit of work performed on the database.
* Must follow **ACID** properties.
* Example: Bank transfer = debit + credit.

---

### **10. What are indexing and its types?**

* Technique to speed up data retrieval using data structures (like B-trees).
* Types: **Primary**, **Secondary**, **Clustered**, **Non-clustered**.

---

## ⚙️ **Top 3 Scenario-Based DBMS Questions (Short Answers)**

---

### **Scenario 1:**

**Q:** Two users try to update the same record at the same time. What happens?
**A:**

* **Concurrency control issue** (lost update).
* Resolved by **locking mechanisms** (shared/exclusive locks) or **timestamp ordering**.
* Example: Only one transaction can hold write lock at a time.

---

### **Scenario 2:**

**Q:** A transaction fails after partially updating multiple tables. What ensures data consistency?
**A:**

* **Atomicity** in ACID ensures rollback of all changes.
* **Log-based recovery** restores database to consistent state.
* Example: Bank debit executed → crash → rollback cancels debit.

---

### **Scenario 3:**

**Q:** A query retrieving data is taking too long. How can you optimize it?
**A:**

* Use **indexes** on frequently searched columns.
* Avoid `SELECT *` (fetch only required columns).
* Use **query optimization** and **proper joins**.
* Analyze using **EXPLAIN PLAN**.

---
