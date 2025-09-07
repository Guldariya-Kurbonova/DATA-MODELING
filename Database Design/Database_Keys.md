🎥 Source: [Types of Keys in Relational Databases (Decomplexify)](https://www.youtube.com/watch?v=8wUUMOKAK-c)  
*These notes follow the explanations in the video, with added reflections for practice.*

---

## Introduction
Relational databases use many types of keys:  
- Primary key  
- Candidate key  
- Superkey  
- Alternate key  
- Foreign key  
- Surrogate key  
- Natural key  
- Simple key  
- Composite key  
- Compound key  
- Intelligent key  

A single key can often belong to multiple categories.  
**Goal:** understand what these terms mean and how they’re used in practice.  

---

## Primary Keys
Example: `US_States` table.  
- `State_Code` (postal abbreviation) is unique and stable → good primary key.  
- PK values must be unique and non-null.  
- Acts as a reliable shorthand for rows (e.g., “the TX row”).  

**Why this matters:**  
Primary keys guarantee row identity and enforce integrity. Choosing a stable PK prevents ambiguity.  

---

## Candidate Keys
- Both `State_Code` and `State_Name` uniquely identify states → both are candidate keys.  
- `State_Capital` fails: capitals can change over time.  
- Keys must uniquely identify not only now but across time.  

**Why this matters:**  
Candidate keys give you options. The best PK balances uniqueness, stability, and simplicity.  

---

## Superkeys
- `{State_Code, Region}` as PK would be wrong → adds unnecessary attributes.  
- A candidate key must be irreducible.  
- A superkey = candidate key + extras.  

**Why this matters:**  
Superkeys matter in theory, but in practice avoid bloated keys—stick to minimal identifiers.  

---

## Alternate Keys
- In `US_States`, both `State_Code` and `State_Name` are candidate keys.  
- One chosen as PK, the other can be enforced as an alternate key.  
- Ensures other identifiers remain unique.  

**Why this matters:**  
Alternate keys prevent duplicates when multiple identifiers matter to business rules.  

---

## Foreign Keys
- Example: `Voters` table with `State_Of_Voter_Registration`.  
- Invalid codes like “QX” must be blocked.  
- Foreign key constraint ensures values match PKs in `US_States`.  

**Why this matters:**  
Foreign keys guarantee referential integrity across tables and make joins reliable.  

---

## Surrogate vs. Natural Keys
- **Natural key:** meaningful in the real world (`State_Code`).  
- **Surrogate key:** arbitrary value meaningful only in the DB (`State_ID`).  
- Surrogates help when no natural key exists (e.g., Recipes).  
- Natural keys are also called business keys.  

**Why this matters:**  
Choosing between surrogate and natural keys is a central design decision. Both have trade-offs.  

---

## Composite vs. Simple Keys
- **Simple key:** one attribute.  
- **Composite key:** multiple attributes (e.g., `{Coffee_Type, Cup_Size}`).  
- Composite PKs create composite FKs in referencing tables.  

**Why this matters:**  
Composite keys are sometimes necessary but increase join complexity.  

---

## Compound Keys
- Sometimes used synonymously with composite.  
- Stricter use: composite key with at least one FK.  
- Example: `Customer_Account` table with PK `{Customer_ID, Account_ID}`.  

**Why this matters:**  
Compound keys are common in link/junction tables for many-to-many relationships.  

---

## Intelligent Keys
- Example: Product codes like `CLS-TRN-016` (Classic, Train set, #16).  
- Natural key with embedded meaning in its parts.  
- Risks:  
  - People rely on extracting meaning from the code.  
  - Re-categorization can break the format.  
- Better: store category/subcategory as separate columns.  

**Why this matters:**  
Intelligent keys are tempting but fragile. They tie business rules too tightly to identifier formats.  

---

## Final Takeaways
- Good design usually involves:  
  - Primary key (stable, simple, natural if possible).  
  - Alternate key(s) for uniqueness.  
  - Foreign keys for relationships.  
  - Surrogates where natural keys don’t exist.  
- Be cautious with composite and intelligent keys — they add complexity and future risk.  
"""
