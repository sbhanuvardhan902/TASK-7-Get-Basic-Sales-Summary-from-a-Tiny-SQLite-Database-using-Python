
# 🧾 Task 7: Basic Sales Summary Using SQLite and Python

## Objective
Use SQL queries within Python to generate a simple sales summary from a SQLite database and visualize it using a bar chart.

---

## Tools Used
- Python
- SQLite (via `sqlite3`)
- pandas
- matplotlib

---

## Dataset
- SQLite database file: `sales_data.db`
- Contains one table: `sales` with columns such as `product`, `quantity`, and `price`

---

## Steps to Execute

### 1️⃣ Load SQLite Database
```python
import sqlite3
conn = sqlite3.connect("sales_data.db")
```
Connects to the SQLite database file using Python's built-in library.

---

### 2️⃣ Run Basic SQL Query
```python
query = "SELECT product, SUM(quantity) AS total_qty, SUM(quantity * price) AS revenue FROM sales GROUP BY product"
```
This query:
- Groups data by product
- Calculates total quantity sold (`total_qty`)
- Calculates total revenue (`revenue` = quantity × price)

---

### 3️⃣ Load Result into pandas
```python
import pandas as pd
df = pd.read_sql_query(query, conn)
```
Executes the SQL query and loads the result into a `DataFrame` for easy handling.

---

### 4️⃣ Print the Results
```python
print(df)
```
Displays the table with product-wise quantity and revenue in the console or notebook.

---

### 5️⃣ Plot a Bar Chart
```python
df.plot(kind='bar', x='product', y='revenue', color='cornflowerblue', legend=False)
plt.title("Revenue by Product")
plt.xlabel("Product")
plt.ylabel("Revenue ($)")
plt.tight_layout()

```
Visualizes the revenue per product using a bar chart.

---

### 6️⃣ Save the Chart (Optional)
```python
plt.savefig("sales_chart.png")
```
Saves the generated chart as a PNG image.

