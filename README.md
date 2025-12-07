# NIKE_Discount_Analysis
Nike Discounts Analytics project built in Databricks. Includes ingestion, cleaning, feature engineering, PySpark analysis, SQL insights, Delta tables, and an interactive dashboard showing discount trends, product price drops, discount ranges, and pricing KPIs.

---

# 📘 **Nike Discounts Analytics – A Story of Pricing, Patterns & Data **

Every product tells a story.
Every discount tells a bigger one.

This project explores **how Nike adjusts its pricing**, how much customers actually save, and how discount behavior varies across hundreds of products.
Using Databricks as the analytical engine, we transformed a simple CSV file into a **full analytical workflow**, complete with notebook exploration, SQL insights, Delta Lake storage, and a fully interactive dashboard.

Welcome to **Nike Discounts Analytics 2025** – where data meets pricing strategy.

---

# 📁 **What You’ll Find in This Repository**

All files are placed directly in the **main branch** for easy access:

| File                                       | What It Represents                                             |
| ------------------------------------------ | -------------------------------------------------------------- |
| **nike_discounts.csv**                     | The story begins here — raw product + pricing + discount data  |
| **Nike_discounts_notebook_analysis.ipynb** | Where data is cleaned, shaped, and explored through PySpark    |
| **Nike_discounts_SQL_analysis.ipynb**      | SQL queries that reveal deep pricing insights                  |
| **Nike_discounts_Analysis.lvdash.json**    | The final dashboard — visual storytelling of discounts         |
| **README.md**                              | This document — your guide to understanding the entire project |

---

# 👟 **The Dataset: Nike Products & Their Discounts**

Imagine scrolling through hundreds of Nike products on sale —
but instead of viewing just prices, you can actually **measure**:

* How deep are the discounts?
* Which product types get the highest cuts?
* What’s the average discount amount?
* Which items still remain expensive even after discounts?
* How do prices shift across categories?

The dataset includes:

* **Product Title**
* **Product Type**
* **Original Price**
* **Discount Amount**
* **Discount Percent**
* **Final Price**

This raw collection becomes far more meaningful as we follow the analytical steps below.

---

# 🧵 **1. Data Ingestion — Bringing the Story Into Databricks**

The CSV file was uploaded to Databricks using:

**Create Table → Upload File**

Inside the notebook, the data was retrieved with:

```python
spark.sql("USE CATALOG workspace")
spark.sql("USE SCHEMA nike_discounts")
df_raw = spark.table("nike_discounts_raw")
```

This gave us the starting point — raw text, messy numbers, missing values.
A story waiting to be cleaned.

---

# 🧼 **2. Data Cleaning & Feature Engineering — Turning Raw Deals into Real Insights**

Inside `Nike_discounts_notebook_analysis.ipynb`, the dataset goes through transformation.

### 🧹 Cleaning Included:

* Converting price columns into numeric values
* Removing empty or corrupted entries
* Fixing product titles & categories
* Standardizing discount values

### 🛠️ Engineering New Features:

To understand discounts better, we created:

* **discount_amount = original_price – final_price**
* **discount_percent (validated)**
* **discount_amount_range** (0–20, 21–40, 41–60, … 100+)
* **price_ratio (final/original)**

These new fields help us see *how good* each discount really is — beyond the surface numbers.

---

# 💾 **3. Delta Storage — Archiving the Clean Story**

To make analytics faster, more reliable, and SQL-ready, we saved the cleaned data as:

```python
df_clean.write.format("delta")
  .mode("overwrite")
  .saveAsTable("workspace.nike_discounts.nike_discounts_clean")
```

Now the dataset is versioned, query-ready, and permanently accessible across Databricks.

---

# 📘 **4. Notebook Analysis — Visualizing Patterns in Real Time**

Using PySpark + Databricks' built-in plotting tools, we explored:

* The distribution of discount percentages
* The range of final prices
* How discount amounts differ across categories
* Which product types receive the steepest discounts

This interactive exploration satisfies the professor’s **Section 4.5 requirement** and gives Gowtham an intuitive understanding of pricing patterns.

---

# 🧮 **5. SQL Analysis — Revealing the Hidden Patterns**

SQL queries were written in `Nike_discounts_SQL_analysis.ipynb`.
The dashboard JSON confirms which queries were used.
Here are the key insights:

### ⭐ Average Discount Percentage


Calculates the typical discount across Nike products.

```sql
SELECT AVG(discount_percent) AS average_discount_percent
FROM workspace.nike_discounts.nike_discounts_clean;
```

### ⭐ Top 10 Highest Discounted Products


Reveals the most aggressively discounted Nike items.

### ⭐ Discount Percent Distribution


Used for pie chart — shows the most common discount levels.

### ⭐ Products with Highest Final Prices


Even with discounts, some products remain premium.

### ⭐ Discount Amount Buckets


A bar chart that tells how many products fall into each discount range.

### ⭐ KPI Metrics



* Average Original Price
* Average Final Price
* Average Discount Amount

These SQL queries form the analytical backbone of the dashboard.

---

# 📊 **6. Dashboard — The Final Story Told Visually**

Exported dashboard: **Nike_discounts_Analysis.lvdash.json**

The dashboard brings the analysis to life:

### 📌 KPI Tiles

* Average Discount %
* Avg Original Price
* Avg Final Price

### 📌 Visual Charts

* **Table:** Top 10 highest discounted Nike products
* **Pie Chart:** Distribution of discount percentages
* **Bar Chart:** Highest final price items
* **Horizontal Bars:** Discount amount ranges

### 📌 Filters

* Multi-select discount percent
* Discount amount range

All visuals come from real SQL queries (metadata extracted from JSON).

---

# 🏁 **7. Closing Summary — What This Project Demonstrates**

Gowtham’s Nike Discounts Analytics project shows complete mastery of the Databricks pipeline:

* ✔ Data ingestion
* ✔ Data cleaning & feature engineering
* ✔ Delta Lake storage
* ✔ PySpark notebook analysis
* ✔ SQL analytics
* ✔ Interactive dashboard creation

It turns a raw pricing CSV into a **business story** — revealing how Nike structures its discounts and where customers find the best deals.


