# NTUC_Capstone_MarketAnalysis (prepared by Yep We Ping)
Retail Customer Purchase Analytics

# Product Sales Dataset 📊

<p align="center">
<img width="280" height="150" alt="image" src="https://github.com/user-attachments/assets/ac0a3d4a-d14b-4831-af0f-bdbd3a97baa0" />

<h1 align="center">Product Sales Analysis

#
Understanding customer purchasing behaviour is essential for driving sustainable business growth. By analysing customer transaction data, organisations can make data-driven decisions to improve marketing effectiveness, customer retention, inventory management, and sales performance.

This study aims to identify purchasing patterns, customer segments, product performance, and sales trends to support business optimisation and revenue growth. The dataset contains detailed information on orders, product categories, geographic regions, and promotional discounts, making it suitable for exploratory data analysis (EDA), sales forecasting, regional market analysis, and data quality improvement.

# Objective
1	Regional Sales Performance & Geographic Market Analysis
	>> Evaluate total revenue, transaction volume, and average order value across different geographic regions (Region) to identify high-performing markets and underperforming zones.
	
2	Impact of Discount Strategies on Net Revenue and Volume
	>> Investigate the relationship between Discount percentages and the resulting Quantity sold versus total net Sales to determine whether discounting successfully stimulates demand or negatively impacts revenue margins.
	
3	Product Demand and Revenue Concentration Analysis
	>> Identify which specific Product lines dominate total revenue generation and sales volume to pinpoint core revenue drivers versus low-performing inventory
	
4	Salesperson Productivity and Performance Benchmarking
	>> Assess individual sales representatives (Salesperson) based on total sales generated, transaction frequency, and average order size to establish performance benchmarks
	
5	Temporal Sales Trends and Demand Seasonality
	>> Examine periodic and monthly variations in sales transactions over time (Date) to detect peak purchasing windows and seasonal demand fluctuations.

## 📋 Dataset Overview

* **File Name:** `product_sales_practice.csv`
* **Time Horizon:** January 2026 – June 2026
* **Target Category:** Electronics
* **Key Entities:** Products, Sales Team, Regional Markets, Revenue Metrics

  Link to Jupyter Notebook in Google Colab:
  https://colab.research.google.com/drive/1zdPR2ig9qFp6Q1gPrZvky3Ac7UITW3Mv?usp=sharing
   
## 🗂️ Data Dictionary

The dataset consists of the following 10 features:

| Column Name | Data Type | Description | Example Value |
| :--- | :--- | :--- | :--- |
| **Order_ID** | String | A unique alphanumeric identifier for each transaction. | `ORD078` |
| **Date** | Date | The transaction date formatted as `YYYY-MM-DD`. | `2026-04-09` |
| **Product** | String | The name of the electronic item sold. | `Laptop`, `Mouse`, `Webcam` |
| **Category** | String | The high-level category classification. | `Electronics` |
| **Region** | String | The geographic sales territory. | `North`, `East`, `West`, `South` |
| **Salesperson** | String | The name of the account representative. | `Alice`, `Bob`, `Charlie`, `Diana`, `Ethan` |
| **Quantity** | Integer | The total units purchased in the order. | `7.0` |
| **Unit_Price** | Float | The retail price per single unit of the product. | `997.67` |
| **Discount** | Float | The promotional deduction percentage applied (0.0 to 0.15). | `0.15` (equivalent to 15%) |
| **Sales** | Float | The final calculated gross revenue earned from the order. | `6983.69` |

## 🔍 Data Quality & Cleaning Notes

If you are using this dataset for data cleaning projects, please note that it intentionally contains realistic real-world data anomalies:
* **Missing Values (NaNs):** Features like `Region`, `Salesperson`, `Unit_Price`, `Discount`, and `Sales` contain scattered missing fields (e.g., missing revenue values or unattributed regional boundaries).
* **Calculated Columns:** The `Sales` column follows the general formula:  
  \[\text{Sales} = (\text{Quantity} \times \text{Unit\_Price}) \times (1 - \text{Discount})\]
  This relationship can be exploited to programmatically restore missing metrics.
* **Empty Rows:** The raw structure contains blank structural divider rows (`,,,,,,,,,`) that should be filtered out during preprocessing.

## 🛠️ Usage Example (Python & Pandas)

Get started analyzing this dataset quickly using Python:

```python
import pandas as pd

# Load the dataset and drop completely empty structural lines
df = pd.read_csv('sales_data.csv').dropna(how='all')

# Convert date column to datetime object
df['Date'] = pd.to_datetime(df['Date'])

# Quick view of total sales revenue by product
revenue_by_product = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
print("Revenue by Product:\n", revenue_by_product)
