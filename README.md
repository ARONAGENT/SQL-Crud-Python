# SQL-CRUD-Project

## Overview
This project demonstrates how to perform CRUD (Create, Read, Update, Delete) operations on a MySQL database using Python. The database is hosted on AWS Cloud, and we use the `pymysql` module for database connectivity. The project includes Jupyter Notebooks covering different SQL operations.

## Prerequisites
Before you begin, ensure you have the following installed:

- Python 3.x
- Jupyter Notebook
- `pymysql` module
- MySQL database hosted on AWS

## 1. Connecting to a MySQL Cloud Database using `pymysql`
To connect to a MySQL database on AWS, follow these steps:

### Step 1: Install `pymysql`
```sh
pip install pymysql
```

### Step 2: Establish a Connection
Use the following Python script to connect to your MySQL database:

```python
import pymysql

# Database connection details
host = "your-db-endpoint"  # AWS RDS or other cloud database endpoint
user = "your-username"
password = "your-password"
database = "your-database-name"

try:
    connection = pymysql.connect(
        host=host,
        user=user,
        password=password,
        database=database
    )
    print("Connected to the database successfully!")
except Exception as e:
    print("Error connecting to database:", e)
```

## 2. SQL Operations Covered in the Project
Each Jupyter Notebook covers a specific operation:

### 01. PythonDBConnection.ipynb
- Establishes a connection to the MySQL cloud database.
- Ensures the database is accessible from Python.

### 02. SelectOperation.ipynb
- Fetches data from the database using `SELECT` queries.
```python
cursor = connection.cursor()
cursor.execute("SELECT * FROM table_name")
rows = cursor.fetchall()
for row in rows:
    print(row)
```

### 03. Search-Operation.ipynb
- Uses `WHERE` clause to search specific records.
```python
cursor.execute("SELECT * FROM table_name WHERE column_name = %s", (value,))
result = cursor.fetchall()
```

### 04. Insert-Operation.ipynb
- Inserts new records into the database.
```python
query = "INSERT INTO table_name (column1, column2) VALUES (%s, %s)"
cursor.execute(query, (value1, value2))
connection.commit()
```

### 05. Update.ipynb
- Updates existing records.
```python
query = "UPDATE table_name SET column1 = %s WHERE column2 = %s"
cursor.execute(query, (new_value, condition))
connection.commit()
```

### 06. Delete.ipynb
- Deletes records from the database.
```python
query = "DELETE FROM table_name WHERE column_name = %s"
cursor.execute(query, (value,))
connection.commit()
```

### 07. Joins.ipynb
- Demonstrates SQL joins (INNER JOIN, LEFT JOIN, etc.).
```python
query = "SELECT a.column1, b.column2 FROM table1 a JOIN table2 b ON a.id = b.id"
cursor.execute(query)
results = cursor.fetchall()
```

### 08. Call Procedure.ipynb
- Calls stored procedures from MySQL.
```python
query = "CALL procedure_name(%s)"
cursor.execute(query, (param,))
```

### 09. Create-table.ipynb
- Demonstrates how to create tables in MySQL.
```python
query = "CREATE TABLE students (id INT PRIMARY KEY, name VARCHAR(255))"
cursor.execute(query)
```

## 3. Clone and Run the Project
### Step 1: Clone the Repository
```sh
git clone https://github.com/ARONAGENT/SQL-Crud-Python.git
cd SQL-CRUD-Project
```

### Step 2: Install Dependencies
```sh
pip install pymysql
```

### Step 3: Run Jupyter Notebook
```sh
jupyter notebook
```
Open the required notebook and follow the instructions inside.

## Conclusion
This project serves as a guide to using MySQL with Python for common database operations. Feel free to modify and expand on it to suit your needs!

