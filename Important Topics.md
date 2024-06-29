# DBMS Important Topics

### 1. DBMS vs Conventional File System
A **Database Management System (DBMS)** is software that manages databases, allowing you to store, modify, and retrieve data efficiently. Examples include MySQL, Oracle, and SQL Server. A **conventional file system** is a method of storing and organizing files on storage devices like hard drives, such as NTFS on Windows or ext4 on Linux.

**Differences:**

- **Data Integrity and Security:**
  - **DBMS:** Has features like data validation, access control, and encryption. For example, a DBMS can ensure that a phone number only contains digits and restricts access to sensitive data.
  - **File System:** Lacks sophisticated data integrity and security features. For instance, a file system cannot prevent a text file from containing invalid data or restrict access based on user roles.

- **Data Redundancy and Consistency:**
  - **DBMS:** Minimizes redundancy through normalization. For example, customer data is stored once and referenced everywhere needed, preventing duplicates.
  - **File System:** High redundancy, with the same data often stored in multiple files, leading to inconsistencies. For instance, customer data might be duplicated across several documents.

- **Concurrent Access:**
  - **DBMS:** Supports multiple users accessing and modifying the database at the same time using locking and transaction mechanisms. For example, two employees can update different parts of the database simultaneously without conflict.
  - **File System:** Struggles with concurrent access, potentially causing data corruption if multiple users modify the same file at the same time.

- **Backup and Recovery:**
  - **DBMS:** Offers robust backup and recovery options, like point-in-time recovery. For example, you can restore the database to its state at any specific time before an error occurred.
  - **File System:** Basic backup options that often require manual intervention. For instance, you need to manually copy files to a backup location.

- **Data Abstraction:**
  - **DBMS:** Provides multiple levels of data abstraction (physical, logical, and view levels). For example, users can interact with data through simple queries without knowing the complex storage details.
  - **File System:** Manages data directly, making it harder to abstract and manage complex data relationships.

### 2. Three Tier Architecture
**Three-tier architecture** divides an application into three layers:

1. **Presentation Layer (Client Tier):** The user interface where users interact with the application. Examples include web browsers and mobile apps. For instance, a web page where users input data into a form.
2. **Application Layer (Business Logic Tier):** Processes business logic and rules. This layer handles data processing and decision-making. For example, a server-side script that processes form data and updates the database.
3. **Data Layer (Database Tier):** Stores and manages data. This layer includes the database server. For instance, a MySQL database storing user information.

### 3. Data Models
**Data models** define how data is structured, stored, and manipulated. Here are some common types:

- **Hierarchical Model:** Organizes data in a tree-like structure. Each record has a single parent and multiple children. For example, an organizational chart where each employee reports to one manager.
- **Network Model:** Uses a graph structure to represent data with multiple parent-child relationships. For instance, a network of roads where a city connects to multiple other cities.
- **Relational Model:** Organizes data into tables with rows and columns. Each table represents an entity, and relationships are established using foreign keys. For example, a table for customers and another for orders, with a customer ID linking orders to customers.
- **Object-oriented Model:** Stores data as objects, similar to object-oriented programming. For example, a customer object with properties like name, address, and orders.

### 4. Meta Data, Data Dictionary
**Metadata** is data about data. It provides information about the structure, format, and other characteristics of a dataset. For example, metadata for a table includes the names of columns, their data types, and constraints like primary keys.

A **Data Dictionary** is a centralized repository that stores metadata. It contains detailed information about the database's structure, such as tables, columns, data types, constraints, and relationships. The data dictionary serves as a reference for database administrators and developers. For example, it might list all the tables in a database, the columns in each table, and the relationships between tables.

### 5. Concept of Redundancy Including Anomalies
**Redundancy** in databases refers to the unnecessary duplication of data. Redundancy can lead to several problems known as anomalies:

- **Update Anomaly:** Occurs when updating redundant data in one place but not in others, leading to inconsistencies. For example, if a customer changes their address and it's updated in one table but not another, the database will have conflicting address information.
- **Insertion Anomaly:** Happens when certain data cannot be inserted into the database without the presence of other related data. For instance, adding a new student to a course table without an existing entry for that student in the student table.
- **Deletion Anomaly:** Arises when deleting data inadvertently causes other important data to be removed. For example, deleting a department might also remove information about all employees in that department if they are stored together.

### 6. Armstrong Axioms
**Armstrong axioms** are a set of rules used to infer all functional dependencies in a database:

1. **Reflexivity:** If Y is a subset of X, then X determines Y (X -> Y). For example, if a set of attributes includes an attribute itself, it naturally determines that attribute.
2. **Augmentation:** If X determines Y (X -> Y), then adding any attributes Z to both sides preserves the dependency (XZ -> YZ). For instance, if knowing a student's ID (X) can determine their name (Y), then knowing the student's ID and their course (XZ) can determine their name and course (YZ).
3. **Transitivity:** If X determines Y (X -> Y) and Y determines Z (Y -> Z), then X determines Z (X -> Z). For example, if knowing a student's ID (X) can determine their name (Y), and knowing their name (Y) can determine their address (Z), then knowing the student's ID (X) can determine their address (Z).

### 7. Concept of Normalization
**Normalization** is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves decomposing tables into smaller, well-structured tables that satisfy certain normal forms:

- **First Normal Form (1NF):** Ensures that each column contains only atomic (indivisible) values and each row is unique. For example, a table with columns for customer ID, name, and address, where each column holds a single value.
- **Second Normal Form (2NF):** Builds on 1NF by ensuring that all non-key attributes are fully functionally dependent on the primary key. It removes partial dependencies, where an attribute is dependent only on part of a composite primary key. For example, a table with a composite key of student ID and course ID, where course details depend only on course ID should be separated.
- **Third Normal Form (3NF):** Ensures that all non-key attributes are not only fully functionally dependent on the primary key but also non-transitively dependent. It removes transitive dependencies, where non-key attributes depend on other non-key attributes. For instance, if a student's department is determined by their department ID, this should be stored separately from the student's personal details.
- **Boyce-Codd Normal Form (BCNF):** A stricter version of 3NF, where every determinant must be a candidate key. For example, if an employee's title determines their department, this dependency should be represented in a separate table if the title itself isn't a candidate key.

### 8. Concept of Dependency
**Dependencies** describe relationships between attributes in a database. The most common type is functional dependency, where one attribute uniquely determines another attribute. For example, in a table of employees, the employee ID determines the employee's name (employee ID -> employee name).

### Concept of Keys in DBMS
Keys are essential for identifying unique records in a database:

- **Primary Key:** A unique identifier for each record in a table. For example, a student ID in a student table.
- **Candidate Key:** A set of attributes that can uniquely identify records in a table. For example, in a table of books, both ISBN and book title could be candidate keys.
- **Foreign Key:** An attribute that creates a link between two tables, referencing the primary key in another table. For example, a student ID in an enrollment table that refers to the student ID in a student table.

### 9. Concept of Indexing
**Indexing** is a technique used to improve the speed of data retrieval operations on a database table. An index is a data structure that allows quick lookup of records based on the values of one or more columns.

Types of indexes:
- **B-tree Index:** Organizes data in a balanced tree structure, allowing fast retrieval, insertion, and deletion operations. For example, a B-tree index on a customer ID can quickly find a customer record.
- **Hash Index:** Uses a hash function to map keys to locations in an array, providing efficient equality searches. For instance, a hash index on a product code can quickly locate a product record.

### 10. SQL Joins
**SQL joins** are used to combine rows from two or more tables based on a related column between them:

- **Inner Join:** Returns rows with matching values in both tables. For example, to find orders with matching customer details, you can join the orders table and

 customers table on the customer ID.
  ```sql
  SELECT orders.order_id, customers.customer_name
  FROM orders
  INNER JOIN customers ON orders.customer_id = customers.customer_id;
  ```

- **Left Join (Left Outer Join):** Returns all rows from the left table and the matched rows from the right table. Rows from the left table without matches in the right table will still be included, with NULL values for columns from the right table. For example, to find all customers and their orders, even if some customers have no orders.
  ```sql
  SELECT customers.customer_name, orders.order_id
  FROM customers
  LEFT JOIN orders ON customers.customer_id = orders.customer_id;
  ```

- **Right Join (Right Outer Join):** Returns all rows from the right table and the matched rows from the left table. Rows from the right table without matches in the left table will still be included, with NULL values for columns from the left table. For instance, to find all orders and the customers who placed them, even if some orders have no associated customers.
  ```sql
  SELECT orders.order_id, customers.customer_name
  FROM orders
  RIGHT JOIN customers ON orders.customer_id = customers.customer_id;
  ```

- **Full Join (Full Outer Join):** Returns rows when there is a match in either table. Unmatched rows from both tables will be included, with NULL values for columns from the table without a match. For example, to find all customers and orders, regardless of whether there is a match between them.
  ```sql
  SELECT customers.customer_name, orders.order_id
  FROM customers
  FULL OUTER JOIN orders ON customers.customer_id = orders.customer_id;
  ```

### 11. ACID Properties
**ACID properties** ensure reliable processing of database transactions:

- **Atomicity:** Ensures that each transaction is treated as a single unit, which either completely succeeds or completely fails. For example, transferring money between two accounts involves debiting one and crediting another. Both actions must succeed or fail together.
- **Consistency:** Ensures that a transaction brings the database from one valid state to another, maintaining database integrity. For example, ensuring that the total amount of money before and after a transaction remains the same.
- **Isolation:** Ensures that transactions occur independently without interfering with each other. For instance, two transactions updating different accounts should not affect each other's operations.
- **Durability:** Ensures that once a transaction is committed, its changes are permanent and survive any subsequent failures. For example, once money is transferred and the transaction is committed, it should remain transferred even if there is a system crash immediately afterward.

### 12. Immediate Updation and Deferred Updation
- **Immediate Updation:** Changes made by a transaction are applied to the database immediately. For example, if a customer places an order, the inventory is updated right away. This approach is suitable for real-time updates but makes rollback operations more complex.
- **Deferred Updation:** Changes made by a transaction are stored temporarily and applied to the database only when the transaction is committed. For instance, if a customer places an order, the inventory is updated only when the transaction is finalized. This ensures that incomplete transactions do not affect the database, simplifying rollback operations but potentially delaying the visibility of updates.

### 13. Finding Candidate Keys, Prime and Non-Prime Attributes, Highest Normal Form
- **Candidate Keys:** To find candidate keys, identify all sets of attributes that can uniquely identify records in a table. These sets must satisfy uniqueness (no duplicate values) and irreducibility (no subset of attributes can still uniquely identify records). For example, in a table of books, both ISBN and book title could be candidate keys if each uniquely identifies a book.
- **Prime Attributes:** Prime attributes are those that are part of any candidate key. For example, if a book table has candidate keys {ISBN} and {title, author}, then ISBN, title, and author are prime attributes.
- **Non-Prime Attributes:** Non-prime attributes are those that are not part of any candidate key. For instance, in the book table, the publication date might be a non-prime attribute if it is not part of any candidate key.
- **Highest Normal Form:** To determine the highest normal form of a table, evaluate the table against normalization rules. Start with the First Normal Form (1NF) and check if the table meets the criteria. Then, proceed to Second Normal Form (2NF), Third Normal Form (3NF), and Boyce-Codd Normal Form (BCNF), evaluating each level's requirements. The highest normal form a table satisfies is its current normalization level. For example, if a table is in 3NF but not in BCNF, its highest normal form is 3NF.


# DBMS Important Q & A


### 1. Database Properties and Advantages of Traditional File Systems

**Database Properties:**
- **Data Integrity:** Ensures the accuracy and consistency of data.
- **Data Security:** Protects data from unauthorized access.
- **Data Redundancy Reduction:** Minimizes data duplication.
- **Data Consistency:** Ensures all users see the same data.
- **Data Sharing:** Allows multiple users to access the data simultaneously.
- **Data Independence:** Separates data from the application programs that use the data.

**Advantages of Traditional File Systems:**
- **Simplicity:** Easy to design and manage for simple applications.
- **Performance:** Can be faster for certain specific tasks due to lower overhead.
- **Flexibility:** Easier to tailor to specific needs without adhering to strict database schemas.

### 2. Different Types of Database Users

- **End Users:** Regular users who interact with the database through application interfaces to perform their tasks. Example: Bank customers using online banking.
- **Application Programmers:** Write application programs that interact with the database. Example: Software developers creating a payroll system.
- **Database Administrators (DBA):** Responsible for managing and maintaining the database system. Example: A professional managing a company's database infrastructure.
- **System Analysts:** Design and develop system specifications. Example: Analysts designing a new data processing system.
- **Database Designers:** Design the database structure. Example: Professionals creating a schema for an e-commerce site.

### 3. DBA and Role of DBA

**Database Administrator (DBA):** A person responsible for managing and maintaining a database system.

**Roles of a DBA:**
- **Installation and Configuration:** Setting up the database software and configuring it for use.
- **Backup and Recovery:** Ensuring data is regularly backed up and can be restored.
- **Security Management:** Implementing access controls to secure data.
- **Performance Monitoring:** Monitoring and optimizing database performance.
- **Data Integrity Management:** Ensuring data remains accurate and consistent.
- **User Management:** Managing user accounts and permissions.
- **Database Maintenance:** Regularly updating and maintaining the database system.

### 4. What is a Database Instance and Schema

- **Database Instance:** The set of information stored in the database at a particular moment. It changes frequently with database operations. Example: The current data in an employee database.
- **Database Schema:** The overall structure of the database, defined during database creation. It remains relatively stable. Example: The design and layout of the employee database tables and relationships.

### 5. Define 3-Tier Architecture of DBMS

**Three-tier architecture** divides the database system into three layers:

1. **Presentation Layer (Client Tier):** The user interface. Example: A web browser displaying a user dashboard.
2. **Application Layer (Business Logic Tier):** Processes business logic and rules. Example: A server running a script to validate user input.
3. **Data Layer (Database Tier):** Stores and manages data. Example: A database server storing user information.

### 6. What is a Relation?

A **relation** in a database is a table consisting of rows and columns. Each row represents a record, and each column represents an attribute of the record. Example: A table "Employees" with columns like EmployeeID, Name, and Department.

### 7. Data Models

**Data Models** describe the structure and relationships of data in a database.

- **Relational Model:** Organizes data into tables (relations) with rows and columns. Example: A table for customers with columns for customer ID, name, and address.
- **Hierarchical Model:** Organizes data in a tree-like structure with parent-child relationships. Example: An organization chart with employees reporting to managers.
- **Entity-Relationship (ER) Model:** Uses entities and relationships to model data. Example: An ER diagram showing customers and their orders.

### 8. What is ER Model?

The **Entity-Relationship (ER) Model** is a conceptual representation of data that describes the relationships between entities in a database. Entities represent objects, and relationships represent associations between these objects. Example: An ER model for a university database with entities like Student, Course, and Instructor, and relationships like Enrolls and Teaches.

### 9. Different Types of Notation in ER Diagram

**ER Diagram Notations:**
- **Rectangles:** Represent entities. Example: A rectangle labeled "Employee."
- **Ovals:** Represent attributes. Example: An oval labeled "EmployeeName."
- **Diamonds:** Represent relationships. Example: A diamond labeled "WorksFor" connecting "Employee" and "Department."
- **Lines:** Connect entities to attributes and relationships. Example: A line connecting "Employee" to "WorksFor."
- **Double Rectangles:** Represent weak entities. Example: A double rectangle labeled "Dependent."
- **Double Lines:** Represent total participation. Example: Double lines connecting "Employee" to "WorksFor."

### 10. What is Weak and Strong Entity Set?

- **Strong Entity Set:** An entity that can be uniquely identified by its attributes alone. Example: A "Customer" entity with a unique customer ID.
- **Weak Entity Set:** An entity that cannot be uniquely identified by its attributes alone and depends on a strong entity. Example: A "Dependent" entity that depends on the "Employee" entity.

### 11. What is Participation in ER Diagram?

**Participation** describes the extent to which entities participate in a relationship:
- **Total Participation:** Every instance of the entity must participate in the relationship. Represented by double lines. Example: Every employee must work for a department.
- **Partial Participation:** Some instances of the entity may not participate in the relationship. Represented by single lines. Example: Not every student may have a scholarship.

### 12. Mapping Cardinality (one to one, one to many, many to one, many to many)

**Mapping Cardinality** describes the number of instances of one entity related to the number of instances of another entity:

- **One to One (1:1):** One instance of entity A is related to one instance of entity B. Example: Each person has one passport.
- **One to Many (1:M):** One instance of entity A is related to many instances of entity B. Example: One teacher teaches many students.
- **Many to One (M:1):** Many instances of entity A are related to one instance of entity B. Example: Many employees work in one department.
- **Many to Many (M:N):** Many instances of entity A are related to many instances of entity B. Example: Many students enroll in many courses.

### 13. What is Aggregation in ER Diagram?

**Aggregation** is a concept in ER modeling where a relationship between entities is treated as a higher-level entity. It is used to express relationships between relationships. Example: If a "Project" involves multiple "Departments" and "Employees," the aggregation might show "WorksOn" (relationship between "Employee" and "Project") being related to "Department."

### 14. What is Generalization and Specialization?

- **Generalization:** Combining similar entities into a single generalized entity. Example: Combining "UndergraduateStudent" and "GraduateStudent" into "Student."
- **Specialization:** Dividing a general entity into more specific entities. Example: Dividing "Vehicle" into "Car" and "Truck."

### 15. Drawing of ER Diagram

An ER diagram visually represents the structure of a database. Here's an example process for creating an ER diagram for a university database:

1. **Identify Entities:** Student, Course, Instructor, Department.
2. **Identify Relationships:** Enrolls (between Student and Course), Teaches (between Instructor and Course), BelongsTo (between Course and Department).
3. **Draw Entities:** Represent entities as rectangles.
4. **Draw Relationships:** Represent relationships as diamonds and connect entities with lines.
5. **Add Attributes:** Add ovals for attributes and connect them to their respective entities.

### SQL

### 16. Group By and Having

**GROUP BY:** Groups rows that have the same values in specified columns into summary rows.

**HAVING:** Applies conditions to groups formed by the GROUP BY clause.

Example: Finding the total salary of employees in each department having a total salary greater than 100,000.

```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department
HAVING SUM(salary) > 100000;
```

### 17. Normal Queries

**Normal Queries:** Basic SQL queries used to retrieve, insert, update, and delete data.

Examples:
- **SELECT:** Retrieve data.
  ```sql
  SELECT * FROM employees;
  ```
- **INSERT:** Add new data.
  ```sql
  INSERT INTO employees (name, department, salary) VALUES ('John Doe', 'IT', 50000);
  ```
- **UPDATE:** Modify existing data.
  ```sql
  UPDATE employees SET salary = 60000 WHERE name = 'John Doe';
  ```
- **DELETE:** Remove data.
  ```sql
  DELETE FROM employees WHERE name = 'John Doe';
  ```

### 18. Types of Languages

**Types of Database Languages:**
- **Data Definition Language (DDL):** Defines the database structure.
  Example: `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`.
  ```sql
  CREATE TABLE employees (id INT, name VARCHAR(100), department VARCHAR(100), salary DECIMAL(10, 2));
  ```
- **Data Manipulation Language (DML):** Manipulates data in the database.
  Example: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
  ```sql
  SELECT * FROM employees;
  ```
- **Data Control Language (DCL):** Controls access to data.
  Example: `GRANT`, `REVOK

E`.
  ```sql
  GRANT SELECT ON employees TO user_name;
  ```
- **Transaction Control Language (TCL):** Manages transactions.
  Example: `COMMIT`, `ROLLBACK`.
  ```sql
  COMMIT;
  ```

### Database Design

### 19. What are Anomalies? And Three Types of Anomalies.

**Anomalies:** Problems in database tables that can cause inconsistency and redundancy.

- **Insertion Anomaly:** Difficulty adding new data. Example: Adding a new student without any enrolled courses.
- **Deletion Anomaly:** Unintended loss of data when deleting other data. Example: Deleting a course might remove the only record of a student's existence.
- **Update Anomaly:** Inconsistencies arising from updating data in multiple places. Example: Updating a student's address in one record but not in others.

### 20. What is Functional Dependency?

**Functional Dependency:** A relationship where one attribute uniquely determines another attribute. Example: In a table with EmployeeID and EmployeeName, EmployeeID functionally determines EmployeeName.

### 21. Different Types of Functional Dependencies

- **Full Functional Dependency:** An attribute is fully functionally dependent on a composite key if it is dependent on the whole key and not just a part of it. Example: {EmployeeID, ProjectID} → HoursWorked.
- **Partial Dependency:** An attribute is dependent on part of a composite key. Example: {EmployeeID, ProjectID} → EmployeeName (partial dependency on EmployeeID).
- **Transitive Dependency:** An attribute is dependent on another attribute through a third attribute. Example: EmployeeID → DepartmentID and DepartmentID → DepartmentName, thus EmployeeID → DepartmentName.

### 22. Trivial and Non-Trivial Functional Dependencies

- **Trivial Dependency:** A functional dependency where an attribute is functionally dependent on a set of attributes that includes itself. Example: {A, B} → A.
- **Non-Trivial Dependency:** A functional dependency where an attribute is functionally dependent on a set of attributes that does not include itself. Example: {A, B} → C.

### 23. Partial, Full, and Transitive Dependencies

- **Partial Dependency:** An attribute depends on part of a composite primary key. Example: {StudentID, CourseID} → StudentName.
- **Full Dependency:** An attribute depends on the entire composite primary key. Example: {StudentID, CourseID} → Grade.
- **Transitive Dependency:** An attribute depends on another attribute that is not a primary key. Example: StudentID → DepartmentID and DepartmentID → DepartmentName, so StudentID → DepartmentName.

### 24. What is Armstrong's Axioms?

**Armstrong's Axioms:** A set of inference rules used to infer all the functional dependencies on a relational database:

1. **Reflexivity:** If Y is a subset of X, then X → Y.
2. **Augmentation:** If X → Y, then XZ → YZ for any Z.
3. **Transitivity:** If X → Y and Y → Z, then X → Z.

### 25. What is Closure Set of Functional Dependencies?

**Closure Set:** The set of all attributes functionally determined by a given set of attributes. It helps determine if a set of attributes can act as a key.

Example: If {A → B, B → C}, then the closure of {A} is {A, B, C}.

### 26. What is Key in Database

**Key:** A set of attributes used to uniquely identify rows in a table.

- **Primary Key:** A unique identifier for a record in a table. Example: EmployeeID.
- **Super Key:** A set of attributes that uniquely identifies a record. Example: {EmployeeID, EmployeeName}.
- **Alternate Key:** A candidate key not chosen as the primary key. Example: EmployeeSSN in a table where EmployeeID is the primary key.
- **Foreign Key:** An attribute that creates a link between two tables. Example: DepartmentID in the Employee table referencing DepartmentID in the Department table.

### 27. How to Find Keys in Closure Set of Functional Dependencies?

To find keys:
1. Compute the closure of each candidate key.
2. Check if the closure includes all attributes in the table.
3. Minimal keys with this property are candidate keys.

### 28. What is Normalization in Database?

**Normalization:** The process of organizing data to reduce redundancy and improve data integrity. It involves dividing large tables into smaller, related tables and defining relationships between them.

### 29. Different Types of Normal Forms

- **1NF (First Normal Form):** Eliminate duplicate columns from the same table and create separate tables for each group of related data.
  - Example: No repeating groups, each cell contains atomic value.
- **2NF (Second Normal Form):** Remove subsets of data that apply to multiple rows and place them in separate tables. Achieved if it is in 1NF and all non-key attributes are fully functional dependent on the primary key.
  - Example: Table with composite key where non-key attributes are dependent on the entire key.
- **3NF (Third Normal Form):** Remove columns that are not dependent upon the primary key. Achieved if it is in 2NF and all attributes are only dependent on the primary key.
  - Example: No transitive dependencies.
- **BCNF (Boyce-Codd Normal Form):** A stricter version of 3NF. Achieved if it is in 3NF and every determinant is a candidate key.
  - Example: If {A, B} → C, then A and B should be candidate keys.

### 30. Difference Between 3NF and BCNF

- **3NF:** A relation is in 3NF if it is in 2NF and no transitive dependencies exist.
- **BCNF:** A relation is in BCNF if it is in 3NF and every determinant is a candidate key. BCNF is stricter than 3NF and deals with certain types of anomalies that 3NF does not.

### 31. What is Dependency Preservation?

**Dependency Preservation:** Ensuring that the decomposition of a database does not lose any functional dependencies. All dependencies are preserved in the decomposed tables.

### 32. What is Lossless and Lossy Decomposition?

- **Lossless Decomposition:** Decomposing a table in such a way that the original table can be reconstructed from the decomposed tables without any loss of information.
- **Lossy Decomposition:** Decomposing a table where information is lost and the original table cannot be perfectly reconstructed.

### 33. What is Transaction Management in Database?

**Transaction Management:** Ensures that database transactions are processed reliably and ensures the database's integrity in multi-user and distributed environments. It uses ACID properties to guarantee transaction reliability.

### 34. What is ACID Property?

**ACID Properties:** Ensure reliable database transactions:

- **Atomicity:** Transactions are all-or-nothing.
- **Consistency:** Transactions bring the database from one valid state to another.
- **Isolation:** Transactions do not interfere with each other.
- **Durability:** Once a transaction is committed, it is permanent.

### 35. What is Physical Storage in Database? RAID

**Physical Storage:** Refers to how data is stored on physical media like hard drives.

**RAID (Redundant Array of Independent Disks):** A technology that combines multiple physical disks into a single logical unit for redundancy and performance improvement.

- **RAID 0:** Striping, improves performance but no redundancy.
- **RAID 1:** Mirroring, provides redundancy but no performance gain.
- **RAID 5:** Striping with parity, balances performance and redundancy.

### 36. What is Join?

**Join:** Combines rows from two or more tables based on related columns.

### 37. Different Types of Join

- **Inner Join:** Returns records with matching values in both tables.
- **Left Join (Left Outer Join):** Returns all records from the left table and matched records from the right table.
- **Right Join (Right Outer Join):** Returns all records from the right table and matched records from the left table.
- **Full Join (Full Outer Join):** Returns records when there is a match in either table.
