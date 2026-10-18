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

* **File Name:** `customer.csv`
* **Target Category:** Customer Directory
* **Key Entities:** Customer ID,First Name, Last Name, Gender, Age, Country, Income

  Link to Google Colab:
  https://colab.research.google.com/drive/10dyunFAxkvDDQb2xrd1I1uPhSzSBA0ZA?usp=sharing
   
## 🗂️ Data Dictionary

The dataset consists of the following 11 features:

| Column Name | Data Type | Description | Example Value |
| :--- | :--- | :--- | :--- |
| **Order_ID** | String | A unique alphanumeric identifier for each transaction. | `ODSHP00001` |
| **Customer_ID** | String | A unique alphanumeric identifier for each customer. | `CS00001` |
| **Order_Date** | Date | The transaction date formatted as `YYYY-MM-DD`. | `2022-05-26` |
| **Product_name** | String | The name of the products sold. | `Furniture` |
| **Description** | String | Description on the product. | `Transform your space with this stylish and functional furniture.` |
| **Price** | Float | The retail price of the product. | `645.52` |
| **Discount** | Float | The deduction on price of the product. | `0.37` |
| **Tax** | Float | The goods and services tax. | `0.02` |
| **Quantity** | int | The unit sold of the product. | `9` |
| **Shipping_cost** | Float | The direct shipment cost for the transaction. | `8.91` |
| **Shipping_date** | Date | The delivery date formatted as `YYYY-MM-DD`. | `2022-05-29` |

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
