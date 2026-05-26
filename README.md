# SQL_Database_Design
 A collection of SQL scripts demonstrating table creation, constraints, and relational design.
# 🗄️ SQL Database Design & Constraints

This repository demonstrates **MySQL DDL commands and constraints** as part of a structured database design assignment.  
It covers database creation, table management, and enforcement of integrity rules through constraints.

---

## 📌 DDL Commands Implemented
- **CREATE**: Database and tables with appropriate data types and relationships  
- **ALTER**:  
  - Add new column (`email`) to Employees  
  - Modify data type of `designation`  
  - Drop `age` column  
  - Rename `hire_date` → `date_of_joining`  
- **RENAME**:  
  - `Departments` → `Departments_Info`  
  - `Location` → `Locations`  
- **TRUNCATE**: Clear all records from Employees table  
- **DROP**: Remove Employees table and database  

---

## 📌 Constraints Applied
- **Departments Table**  
  - `department_id` as unique identifier (Primary Key)  
  - `department_name` with NOT NULL and UNIQUE constraints  

- **Locations Table**  
  - Auto‑incremented unique identifiers for each location  
  - Prevent null and duplicate entries  

- **Employees Table**  
  - `employee_id` as distinct identifier (Primary Key)  
  - `name` must always be provided (NOT NULL)  
  - `gender` restricted to values `'M'` or `'F'` (CHECK)  
  - `age` must be ≥ 18 (CHECK)  
  - `date_of_joining` defaults to current date if not specified  
  - Foreign Keys:  
    - `department_id` → Departments_Info  
    - `location_id` → Locations  

---

## 📂 Example Script

```sql
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    gender CHAR(1) CHECK (gender IN ('M','F')),
    age INT CHECK (age >= 18),
    designation VARCHAR(100),
    email VARCHAR(100),
    department_id INT,
    location_id INT,
    date_of_joining DATE DEFAULT CURRENT_DATE,
    FOREIGN KEY (department_id) REFERENCES Departments_Info(department_id),
    FOREIGN KEY (location_id) REFERENCES Locations(location_id)
);

OUTPUT SCREEN
<img width="1401" height="792" alt="S" src="https://github.com/user-attachments/assets/e9f6a602-1561-4ea7-a6fb-3e5ac8ea5d88" />

CONSTRAINT and ALTERATION EXAMPLE OUTPUT
<img width="1600" height="850" alt="Alteration" src="https://github.com/user-attachments/assets/7b686d69-8bf2-441d-aba5-409d602275fc" />
<img width="1590" height="772" alt="CONSTRAINT" src="https://github.com/user-attachments/assets/ac17c4c4-cbfb-40be-b765-960de8cee125" />

RELATIONSHIP DIAGRAM
<img width="1588" height="818" alt="ERR employee_db" src="https://github.com/user-attachments/assets/5c666bad-0252-4511-be23-5bb855db1d92" />








