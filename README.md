# 99Bikes Excel project

This project presents an end-to-end data analytics workflow using the **99Bikes dataset** extracted from [Kaggle](https://www.kaggle.com/datasets/tforsyth/99bikes-sales-data). The goal is to showcase real-world Excel-based data analysis and dashboard design by applying core data science steps: **data cleaning**, **pivot table modeling**, and **KPI dashboard creation**.

- `excel-project-99Bikes/`
  - `datasets/` – All data, pivots & dashboards
    - `raw/`
      - `99Bikers_Raw_data.xlsx`
    - `cleaned/`
      - `cleaned_99bikes_data.xlsx`
  - `visuals/`
    - `Customer Analysis Dashboard.png` – Dashboard
    - `customer_pivot_table_preview.png` – Pivot structure
    - `Sales Dashboard.png` – Dashboard
    - `sales_pivot_table_preview.png` – Pivot structure
---

## 📦 Dataset Overview

- **Source**: [Kaggle - 99Bikes Sales Dataset](https://www.kaggle.com/datasets/heeraldedhia/99bikes-sales-data)
- **Sheets Included**:
  - `Transactions`: sales transactions with date, brand, product info
  - `CustomerDemographic`: customer age, gender, wealth, tenure, etc.
  - `CustomerAddress`: location and postcode info
  - `NewCustomerList`: prospective customer records (not used in final dashboard)

---

## 🧼 Data Cleaning & Preparation

- Replaced the following columns with `'Unknown'` where values were null:
  - `last_name`
  - `job_title`
  - `job_industry_category`
  - `brand`
  - `product_line`
  - `product_class`
  - `product_size`

- Mapped values in `online_order`:
  - `1.0` → `'Yes'`
  - `0.0` → `'No'`

- Dropped rows with null `standard_cost`  
  *(also indirectly removed rows with null `product_first_sold_date`)*

- Dropped the `default` column

- Filled null values in `tenure` with `-1`

- Filled null values in `DOB` with `'1/1/1600'`

- Standardized `state` values:
  - `'New South Wales'` → `'NSW'`
  - `'Victoria'` → `'VIC'`

- Cleaned `gender` column:
  - `'F'`, `'Femal'` → `'Female'`
  - `'M'` → `'Male'`
  - `'U'` → `'Unknown'`

- Converted `deceased_indicator`:
  - `'N'` → `'No'`
  - `'Y'` → `'Yes'`

---

## 📊 Pivot Table KPIs

### 🔹 **Sales Analysis (Pivot Tables)**
- Total Revenue = Sum of `list_price` where `order_status = Completed`
- Total Orders = Count of `transaction_id` for completed orders
- Average Sale per Customer = Total Revenue ÷ Distinct `customer_id`
- Monthly Sales Trend = Revenue grouped by Month-Year of `transaction_date`
- Sales by Product Line = Sum of revenue by `product_line`
- Sales by Brand = Top 5 brands by revenue
- Online vs Offline Sales = Revenue by `online_order` flag

### 🔹 **Customer Insights (Pivot Tables)**
- Customers by Wealth Segment = Count of `customer_id` by `wealth_segment`
- Top Customer States = Count by `state`
- Car Ownership Breakdown = Count of `owns_car` ("Yes", "No", "Unknown")
- Average Tenure = Mean of `tenure` (excluding -1)

---

## 📈 Dashboards (Excel)

### 📌 `Sales Dashboard`
- KPI Cards: Total Revenue, Total Orders, Average Order Value
- Line Chart: Monthly Sales Trend
- Pie Chart: Sales by Product Line
- Bar Chart: Top 5 Brands
- Pie Chart: Online vs Offline Revenue

### 📌 `Customer Analysis Dashboard`
- KPI Card: Average Customer Tenure
- Pie Chart: Customers by Wealth Segment
- Pie Chart: Car Owners vs Non-Owners
- Bar Chart: Top 4 States by Customer Count

Each dashboard uses **slicers** for filtering by product line, state, and sales channel.

---

## ⚙️ Tools Used

| Tool      | Purpose                         |
|-----------|---------------------------------|
| **Excel** | Data cleaning, pivots, dashboards |
| Power Query | Null handling, date parsing     |

---

## 🖼 Previews

Find all screenshots in the `visuals/` folder, including:
- `dataset_preview.png`
- `pivot_tables_preview.png`
- `sales_dashboard_preview.png`
- `customer_dashboard_preview.png`

---

## ✅ How to Use

1. Clone or download the repo
2. Open `workbook/99bikes_dashboard_full.xlsx`
3. Navigate to `Sales Dashboard` and `Customer Dashboard` sheets
4. Use slicers to interactively explore the data

---

