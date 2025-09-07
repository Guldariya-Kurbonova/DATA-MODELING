# Database Normalization — Notes from Video

Source: [Database Normalization (YouTube)](https://www.youtube.com/watch?v=ZBgXb66Ckz0&t=8s)

---

## 1. Why Normalization?

- Normalization = process of refining database design to reduce **anomalies** and ensure data integrity.
- Bridges the gap between **logical design** and **physical implementation**.
- Goal: create a design that avoids redundancy, prevents errors, and reflects business rules.

---

## 2. Common Data Anomalies

1. **Insertion Anomaly**  
   - Occurs when new data can’t be added without other unnecessary or unavailable data.  
   - Example: New employee can’t be added until they are assigned a project.  

2. **Update Anomaly**  
   - Same piece of information stored in multiple places → must be updated everywhere.  
   - Risk: inconsistencies when one record is updated but others aren’t.  

3. **Deletion Anomaly**  
   - Removing a record accidentally deletes vital information.  
   - Example: Deleting the only employee on a project → project record is lost.  

**Takeaway:** Normalization prevents these anomalies by restructuring data into proper tables and relationships.

---

## 3. Normal Forms (NF)

## First Normal Form (1NF)

**From the video:**  
- Repeating Values: in order to get rid of that we’re going to have to move our tracks to a new table.  
- So here we have a new table for our tracks: we put the name of the track and the album title is referencing the album table.  
- Now in our album table we don’t have a list of tracks; instead they’re all in the track table, which references back to the album.  

**Why this matters:**  
Without 1NF, you end up with lists or arrays in columns (e.g., multiple phone numbers in one field). That makes querying and updating data a nightmare.

---

## Second Normal Form (2NF)

**From the video:**  
- Second normal form removes what we call functional dependencies, which are groups of columns that depend on each other rather than on the key of the table.  
- One way to look at this is themes or sub-themes of the data.  
- Example: tracks, track title, artist, and artist country group together separate from the album itself.  
- Many albums contain multiple artists. So we add a primary key to the album and track tables, and we move the album artist over to the track table.  

**Why this matters:**  
If you don’t fix partial dependencies, you duplicate artist info across many rows. Updating or correcting it later becomes inconsistent and error-prone.

---

## Third Normal Form (3NF)

**From the video:**  
- To move to third normal form we have to move transient dependencies, which are more subtle.  
- A transient dependency is where a field depends more on another column for its meaning than the table key.  
- Example: artist country does not depend on the track; it depends on the artist itself.  
- So we create an artist table, and tracks now reference both the album and the artist that wrote the album.  
- In the ER diagram: album ↔ tracks, and artist ↔ tracks. Notice there are no many-to-many relationships anymore.  

**Why this matters:**  
3NF eliminates hidden dependencies that cause duplication. Without it, a single typo in “Artist Country” spreads inconsistencies everywhere.

---

## Boyce–Codd Normal Form (BCNF)

**From the video (in later slides):**  
- A stricter version of 3NF.  
- Ensures that every determinant is a candidate key.  
- Helps resolve special cases where 3NF alone does not eliminate redundancy.  

**Why this matters:**  
BCNF is about handling tricky cases that slip past 3NF. It ensures cleaner relationships when multiple candidate keys exist.

---

## Fourth Normal Form (4NF)

**From the video (informal explanation):**  
- Removes multi-valued dependencies.  
- If you have two or more independent multivalued facts about an entity, they must go in separate tables.  
- Example in practice: an artist can play multiple instruments and record multiple genres. Don’t store both in the same table.  

**Why this matters:**  
Without 4NF, one row is trying to carry two independent sets of facts, leading to messy duplication.

---

## Fifth Normal Form (5NF)

**From the video:**  
- Removes join dependencies.  
- A table should not require being reconstructed from multiple smaller tables unless necessary.  
- Common example: Supplier → Part → Project relationships.  

**Why this matters:**  
5NF ensures the design avoids hidden redundancies that appear only when combining multiple relationships.

---

## Sixth Normal Form (6NF)

**From the video:**  
- Deals with temporal data (time-variant facts).  
- Example: Employee salary history — you need to know not only the current salary but also when it was valid (StartDate, EndDate).  
- Rarely needed in day-to-day transaction systems, but very useful in data warehouses and auditing systems.  

**Why this matters:**  
6NF preserves historical accuracy. Without it, you overwrite old facts and lose the ability to see “what was true at a given time.”

---

## 5. Practical Guidelines

- Many-to-Many (M:N) relationships require **linking tables** (e.g., `Invoice` ↔ `Item` → `LineItem`).
- Foreign Keys always go on the **many** side of a relationship.
- Use ER diagrams to visualize normalization steps.  
- Documentation is critical: track changes across versions of ER diagrams.

---

## 6. Thought Process for Normalization

1. Identify anomalies.  
2. Check for repeating groups (fix with 1NF).  
3. Check for functional dependencies (fix with 2NF).  
4. Check for transitive dependencies (fix with 3NF).  
5. Decide if denormalization is needed for performance.  

---

