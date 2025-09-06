# Logical Database Design – Learning Notes

**Video Reference:** [Logical Database Design – YouTube](https://www.youtube.com/watch?v=ZBgXb66Ckz0&t=8s)  
*These notes are based on insights from this video.*

---

## 1. Overview

- **Logical design:** Focuses on *what data needs to be stored* and *how it relates*, independent of any DBMS (Oracle, MySQL, etc.).  
- **Physical design:** Adapts the logical design to a specific DBMS, considering features, constraints, and storage.  
- **Key mindset:** Separate conceptual understanding from technical limitations.  

**Takeaway:** Think first about *what the data represents*, not how the database will implement it.

---

## 2. Core Concepts

- **Entity:** Something to track (person, place, thing) → becomes a table in physical design.  
  - *Example:* `Book`, `Author`, `Employee`  
- **Attribute:** A property of an entity → becomes a column.  
  - *Example:* `Title`, `ISBN`, `EmployeeLastName`  
- **Primary Key (PK):** Unique identifier for each record.  
  - *Natural Key:* Exists in the real world (e.g., ISBN).  
  - *Surrogate Key:* Artificially created (e.g., AuthorID).  
- **Foreign Key (FK):** Links one entity to another; establishes relationships.  

**Tip:** Always consider uniqueness and clarity when choosing primary keys.

---

## 3. Entity Relationships

- **One-to-One (1:1):** Rare; used to:  
  - Avoid storing nulls.  
  - Separate sensitive info for security.  
  - *Example:* `Employee ↔ Payroll` (one employee has one payroll record).  
- **One-to-Many (1:N):** Most common.  
  - *Example:* `Library` → `Books`  
  - One `Library` can have many `Books`.  
  - Each `Book` belongs to exactly one `Library`.  
- **Many-to-Many (M:N):** Allowed in logical design but requires linking tables in physical design.  
  - *Example:* `Students ↔ Courses`.  

**Thought:** Understanding cardinality prevents database errors and ensures the design matches business rules.

---

## 4. ER Diagrams

- Tool for visualizing entities, attributes, and relationships.  
- **Common notations:**  
  - **Arrowhead:** Simple linking  
  - **Crow’s Foot:** Shows min/max cardinality  
  - **Min/Max:** Shows exact ranges (e.g., 1–3 subjects for a book)  

**Tip:** ER diagrams serve as references for physical design, normalization, and SQL creation.

---

## 5. Naming Conventions & Best Practices

- **Tables:** Singular nouns (`Book`, not `Books`).  
- **Attributes:** Unique, descriptive (`EmployeeLastName`).  
- **Primary Keys:** Consistent naming (`TableNameKey`).  
- **Foreign Keys:** Match the primary key they reference.  
- **Avoid spaces:** Use CamelCase (`EmployeeKey`).  

**Thought:** Consistency avoids confusion and makes design maintainable.

---

## 6. Null Values

- Null = absence of data, not zero.  
- Nulls can cause errors in queries and functions.  
- One-to-One relationships help minimize nulls by splitting entities logically.

---

## 7. Notes on Thought Process

When taking logical design decisions:  
1. Identify entities (major nouns).  
2. Identify attributes that describe entities.  
3. Determine relationships between entities.  
4. Define primary keys for uniqueness.  
5. Use ER diagrams to visualize everything.  
6. Document business rules and rationale.  

**Key mindset:** Think conceptually first, implementation later.

---

## 8. Documentation Importance

- ER diagrams and notes are living documents.  
- Useful for:  
  - Physical design  
  - Normalization  
  - SQL generation  
  - Collaboration or review  

**Thought:** Good documentation is as valuable as the database itself.




