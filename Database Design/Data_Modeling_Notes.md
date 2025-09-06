# Logical Database Design – Learning Notes

**Video Reference:** [Logical Database Design – YouTube](https://www.youtube.com/watch?v=ZBgXb66Ckz0&t=8s)  
*These notes are based on insights from this video.*

---

## 1. Overview

- **Logical Design:** Focuses on *what data needs to be stored* and *how entities relate*, independent of any DBMS (e.g., MySQL, PostgreSQL).  
- **Physical Design:** Adapts the logical design to a specific DBMS, considering features, constraints, and storage.  
- **Key Mindset:** Separate conceptual understanding from technical limitations.

---

## 2. Core Concepts

- **Entity:** Represents a real-world object or concept (e.g., `Department`, `Employee`).  
- **Attribute:** A property or characteristic of an entity (e.g., `DeptName`, `EmpID`).  
- **Primary Key (PK):** Uniquely identifies each record in a table.  
  - *Natural Key:* Exists in the real world (e.g., ISBN for books).  
  - *Surrogate Key:* Artificially created (e.g., `AuthorID`).  
- **Foreign Key (FK):** Links one entity to another; establishes relationships.

---

## 3. One-to-Many (1:N) Relationship

- **Definition:** One record in a table (parent) can relate to multiple records in another table (child), but each child record relates to exactly one parent.  
- **New Example:** `Library` → `Books`  
  - One `Library` can have many `Books`.  
  - Each `Book` belongs to exactly one `Library`.  

**ER Diagram Representation:**

