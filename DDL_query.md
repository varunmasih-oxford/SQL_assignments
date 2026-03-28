# Data Definition Language ()

### Common DDL Commands:

* CREATE
* ALTER
* DROP
* TRUNCATE
* RENAME

---

## Step 1: Create Database

```sql
CREATE DATABASE company_db;
USE company_db;
```

---

## Step 2: Create Table

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
```

---

## Step 3: Insert Sample Data (for testing)

```sql
INSERT INTO employees VALUES
(1, 'Amit', 'IT', 50000),
(2, 'Sara', 'HR', 40000);
```

---

## Step 4: ALTER TABLE (Modify Structure)

### Add Column

```sql
ALTER TABLE employees
ADD email VARCHAR(100);
```

### Modify Column

```sql
ALTER TABLE employees
MODIFY salary DECIMAL(12,2);
```

### Rename Column (MySQL Syntax)

```sql
ALTER TABLE employees
CHANGE name full_name VARCHAR(50);
```

### Drop Column

```sql
ALTER TABLE employees
DROP COLUMN department;
```

---

## Step 5: Rename Table

```sql
RENAME TABLE employees TO staff;
```

---

## Step 6: Truncate Table

```sql
TRUNCATE TABLE staff;
```

---

## Step 7: Drop Table

```sql
DROP TABLE staff;
```

---
