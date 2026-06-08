# DecodeLabs_Task3

# Product Sales Analysis – SQL Based Analysis

# Project Overview
This project performs a comprehensive sales analysis on an e‑commerce dataset using SQL.  
The goal is to uncover business insights such as:
- Top‑performing product categories
- Highest / lowest order values
- Monthly revenue trends
- Category contribution to total revenue

The analysis is based on **1,201 orders** recorded between 2023 and 2025.

# Dataset
- **File:** `cleaned_dataset.csv`  
- **Rows:** 1,201  
- **Columns (original):**  
  `orderid`, `date`, `customerid`, `product`, `quantity`, `unitprice`, `shippingaddress`, `paymentmethod`, `orderstatus`, `trackingnumber`, `itemsincart`, `couponcode`, `referralsource`, `totalprice`

- In the SQLite database, columns are renamed `c1` … `c14` for simplicity.

#  Database Used
- **SQLite (Online)** – e.g., [SQLite Online](https://sqliteonline.com/) or any local SQLite environment.

# Tools & Technologies
| Tool | Purpose |
|------|---------|
| SQLite | Data storage and query execution |
| CSV | Raw data format |
| SQL | Data analysis (aggregations, sorting, filtering) |

# How to Run / Use
1. **Open SQLite Online** (or install SQLite locally).  
2. **Import the CSV file** as a table named `Product_Data`.  
   - *Note:* If column names become `c1`…`c14`, map them accordingly.  
3. **Run the following SQL queries** (examples):

# SQL Queries
-- Total records
SELECT COUNT(*) FROM Product_Data;

-- Top 5 highest order values (handle text numbers)
SELECT c14 FROM Product_Data ORDER BY CAST(c14 AS REAL) DESC LIMIT 5;

-- Total revenue per category
SELECT c4, SUM(CAST(c14 AS REAL)) FROM Product_Data GROUP BY c4;

-- Monthly revenue (June 2024 peak)
SELECT strftime('%Y-%m', c2) AS month, SUM(CAST(c14 AS REAL)) AS revenue
FROM Product_Data
GROUP BY month
ORDER BY revenue DESC;

# Key Findings

- Total Orders: 1,201 records.

- Highest Order Values: $3,456.40, $3,390.95, $3,390.80, $3,384.90, $3,370.20 – all from quantity‑5 bulk purchases (Tablets, Laptops, Chairs).

- Lowest Order Values: $11.39, $14.06, $17.24, $17.98, $18.20 – single low‑cost items or promotional sales.

- Top Revenue Category: Chair ($195,620), followed closely by Printer ($195,613) and Laptop ($192,127).

- Average Order Value: Laptop leads ($1,111), Phone lowest ($973).

- Peak Sales Month: June 2024 ($68,069) – potential seasonal or promotional spike.

- Category Contribution: Balanced (12%–15.5%), showing no over‑reliance on a single product.


 # Conclusion
 
The dataset reveals a healthy, diversified sales pattern. High‑value orders drive revenue through bulk purchases, while low‑value orders likely serve customer acquisition. June 2024’s peak warrants further investigation. Proper handling of numeric data stored as text (using CAST or +0) was essential for accurate sorting and aggregation.

# Author

**Zulqarnain Talpur**
**Data Analytics Intern**
**DecodeLabs Industrial Training Program.**
