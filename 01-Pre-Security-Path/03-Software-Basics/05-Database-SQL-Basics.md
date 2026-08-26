# 🗄️ Introduction to Databases & SQL

---

## 📌 1. Fundamentals of Data & Databases

A **Database** is a structured, digital system designed to store, manage, and query information efficiently. 
* **Persistence:** Unlike volatile computer RAM, databases retain information permanently even after system shutdowns.
* **Scalability:** Simple flat files (notebooks, text files, spreadsheets) become slow and prone to errors as data grows. Databases allow quick searching, filtering, and sorting across millions of records.

Information within relational databases is organized into **Tables**.

---

## 📦 2. Core Structure: Tables, Rows, and Columns

Relational database tables structure data in a grid layout similar to spreadsheets.

* **Columns (Attributes):** Vertical fields that define the type of data being stored (e.g., `id`, `drink`, `price`, `time`).
* **Rows (Records):** Horizontal entries that represent a single, complete set of related information (e.g., one specific café order).

| Term | Analogy | Description |
| :--- | :--- | :--- |
| **Table** | Notebook / Spreadsheet | The main container for a specific category of data. |
| **Column** | Header / Category | Defines one specific attribute type across all records. |
| **Row** | Single Entry | Represents a unique complete record inside the table. |

---

## 🔍 3. Asking Questions With SQL

**Structured Query Language (SQL)** is the standard language used to request, filter, and manipulate data stored in relational databases.

### Basic SQL Commands
* **`SELECT`:** Specifies which columns to retrieve. Using `*` selects all available columns.
* **`FROM`:** Specifies the table from which data should be retrieved.
* **`WHERE`:** Filters rows based on defined logical conditions.
* **`ORDER BY`:** Sorts the resulting records by a specified column in ascending (`ASC`, default) or descending (`DESC`) order.

---

## 💻 4. Practical Query Examples

### 1. View All Records (`SELECT * FROM`)
Retrieves every column and row from the `Orders` table.

```sql
SELECT * FROM Orders;
```

---

### 2. Retrieve Specific Columns
Displays only the requested drink and price fields.

```
SELECT drink, price FROM Orders;
```

---

### 3. Filter Records (WHERE)
Extracts only records where the drink field matches the exact string 'Coffee'.

```
SELECT * FROM Orders WHERE drink = 'Coffee';
```

---

### 4. Sort Query Results (ORDER BY)
Sorts records by price in descending order (highest to lowest).

```
SELECT * FROM Orders ORDER BY price DESC;
```

### 5. Combine Filtering and Sorting
Filters for 'Coffee' entries first, then sorts the filtered results by price from highest to lowest.

```
SELECT * FROM Orders WHERE drink = 'Coffee' ORDER BY price DESC;
```

## 🛡️ 5. Security Perspective
From a cybersecurity standpoint, understanding database structures and query mechanics is critical for identifying data exposure risks and backend vulnerabilities.

🔍 Security Analysis Points
Broken Access Control & Unauthorized Data Modification:

If authorization controls are missing, malicious actors can execute unauthorized queries to alter, manipulate, or delete database entries (such as altering financial order amounts or wiping entire tables), leading to data corruption and business loss.

SQL Injection (SQLi) Vulnerabilities:

When user input is directly concatenated into dynamic SQL queries without sanitization or parameterized inputs, attackers can inject malicious SQL statements. This allows unauthorized data exfiltration, authentication bypass, or full database compromise.

Information Disclosure & Over-Fetching:

Executing broad queries like SELECT * without restrictive column parameters or WHERE filters can inadvertently expose sensitive data fields (e.g., personally identifiable information or password hashes) to unauthorized application endpoints.

Data Integrity & Audit Trail Deficiencies:

Without proper transaction logging and access controls, unauthorized database tampering leaves no audit trail, preventing security teams from accurately investigating security breaches or verifying historical data accuracy.
