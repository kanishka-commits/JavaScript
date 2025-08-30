# DBMS Fundamentals Q&A 

---

## 📌 Table of Contents
1. [Basics of DBMS](#1-basics-of-dbms)  
2. [SQL & Queries](#2-sql--queries)  
3. [Keys & Constraints](#3-keys--constraints)  
4. [Normalization & ER Modeling](#4-normalization--er-modeling)  
5. [Indexing & Performance](#5-indexing--performance)  
6. [Transactions & Concurrency](#6-transactions--concurrency)  
7. [Storage & Recovery](#7-storage--recovery)  
8. [Misc / Advanced Basics](#8-misc--advanced-basics)  

---

## 1. Basics of DBMS

- **Q1. What is a DBMS? How is it different from a file system?**  
  - DBMS → software to store, manage, retrieve data efficiently.  
  - File system → simple storage, no data integrity, redundancy issues.  

- **Q2. Advantages of DBMS?**  
  - Reduced data redundancy, improved consistency, security, concurrent access, backup & recovery.  

- **Q3. Types of DBMS?**  
  - Hierarchical, Network, Relational (RDBMS), Object-oriented.  

- **Q4. What is a relational model?**  
  - Data stored in tables (relations) with rows (tuples) and columns (attributes).  

- **Q5. Database schema vs instance?**  
  - Schema → structure of database (fixed).  
  - Instance → actual data at a particular time.
 
- **What are tables, rows, and columns?**
  - Table = collection of rows (records) and columns (attributes). Row = single record, Column = attribute of record.

---

## 2. SQL & Queries

- **Q6. Difference between DDL, DML, DCL, TCL?**  
  - DDL → CREATE, ALTER, DROP (structure)  
  - DML → SELECT, INSERT, UPDATE, DELETE (data)  
  - DCL → GRANT, REVOKE (permissions)  
  - TCL → COMMIT, ROLLBACK (transactions)  

- **Q7. INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN?**  
  - INNER → only matching rows  
  - LEFT → all rows from left + matched from right  
  - RIGHT → all rows from right + matched from left  
  - FULL OUTER → all rows from both tables  

- **Q8. WHERE vs HAVING?**  
  - WHERE → filters rows **before aggregation**  
  - HAVING → filters **after aggregation**  

- **Q9. Subquery: Correlated vs Non-correlated?**  
  - Correlated → depends on outer query, evaluated per row  
  - Non-correlated → independent, runs once  

- **Q10. UNION vs UNION ALL?**  
  - UNION → removes duplicates  
  - UNION ALL → keeps duplicates  

- **Q11. Views?**  
  - Virtual table based on query, does not store data physically  

- **Q12. Stored procedures, triggers, functions?**  
  - Stored procedure → precompiled SQL statements  
  - Trigger → automatically executed on events  
  - Function → returns value, can be used in queries  

---

## 3. Keys & Constraints

- **Q13. Primary key?** → Unique identifier for table row, cannot be NULL.  
- **Q14. Foreign key?** → References primary key in another table for referential integrity.  
- **Q15. Candidate key, alternate key, super key?**  
  - Super key → uniquely identifies a row  
  - Candidate key → minimal super key  
  - Alternate key → candidate key not chosen as primary key  
- **Q16. Unique key vs Primary key?** → Unique allows NULLs (in most DBMS), Primary does not.  
- **Q17. Constraints?** → Rules on table data: NOT NULL, UNIQUE, CHECK, DEFAULT, PRIMARY, FOREIGN.  

---

## 4. Normalization & ER Modeling

- **Q18. What is normalization?** → Process to remove redundancy and dependency.  
- **Q19. 1NF, 2NF, 3NF, BCNF?**  
  - 1NF → atomic attributes  
  - 2NF → 1NF + no partial dependency  
  - 3NF → 2NF + no transitive dependency  
  - BCNF → stricter 3NF, resolves anomalies in composite keys  

- **Q20. Denormalization?** → Combining tables to improve query performance.  
- **Q21. ER diagram?** → Visual representation: entities, attributes, relationships.  
- **Q22. Weak vs Strong entities?** → Weak depends on strong entity, has partial key.  

---

## 5. Indexing & Performance

- **Q23. Index?** → Data structure to speed up retrieval.  
- **Q24. Clustered vs Non-clustered index?**  
  - Clustered → table rows stored in index order  
  - Non-clustered → separate index points to rows  

- **Q25. B-Tree index?** → Balanced tree, logarithmic search time.  
- **Q26. Hash index?** → Uses hash function for quick lookup, no order guaranteed.  
- **Q27. Pros & cons of indexing?**  
  - Pros: Faster search  
  - Cons: Slower insert/update/delete, extra storage  

---

## 6. Transactions & Concurrency

- **Q28. Transaction?** → Logical unit of work on DB, all-or-nothing.  
- **Q29. ACID properties?**  
  - Atomicity → all or nothing  
  - Consistency → maintains DB constraints  
  - Isolation → concurrent transactions don’t interfere  
  - Durability → committed data persists  

- **Q30. Commit & Rollback?** → Commit saves changes, Rollback undoes changes.  
- **Q31. Concurrency control?** → Prevents conflicts when multiple transactions run.  
- **Q32. Pessimistic vs Optimistic control?**  
  - Pessimistic → locks resources  
  - Optimistic → checks for conflicts before commit  

- **Q33. Deadlock in DB?** → Two transactions wait for each other’s locks → no progress. Resolved using wait-die/wound-wait or timeout.  

---

## 7. Storage & Recovery

- **Q34. Database storage structure?** → Tablespaces → Pages → Blocks  
- **Q35. Log-based recovery?** → Uses transaction logs to recover DB after crash  
- **Q36. Backup types?** → Full, Incremental, Differential  
- **Q37. Replication vs Mirroring?** → Replication → copies DB to multiple nodes  
  - Mirroring → real-time exact copy  

---

## 8. Misc / Advanced Basics

- **Q38. OLTP vs OLAP?** → OLTP → transactions, frequent updates  
  - OLAP → analytics, read-heavy  

- **Q39. SQL vs NoSQL?** → SQL → structured, relational  
  - NoSQL → unstructured, document/column/key-value  

- **Q40. Relation, Tuple, Attribute?** → Table = relation, row = tuple, column = attribute  
- **Q41. Foreign key cascade update/delete?** → Automatically updates/deletes referencing rows  
- **Q42. Soft delete vs hard delete?** → Soft → mark as deleted  
  - Hard → remove from DB  

---
