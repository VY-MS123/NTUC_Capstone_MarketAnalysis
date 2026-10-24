# NTUC_Capstone_MarketAnalysis (prepared by Yep We Ping)
Retail Customer Purchase Analytics

# Product Sales Dataset 📊

<p align="center">
<img width="280" height="150" alt="image" src="https://github.com/user-attachments/assets/ac0a3d4a-d14b-4831-af0f-bdbd3a97baa0" />

<h1 align="center">Product Sales Analysis

#
Understanding customer purchasing behaviour is essential for sustainable growth. This project analyses customer and transaction data to identify purchasing patterns, customer segments, product performance and sales trends that support revenue growth and better marketing, retention and inventory decisions.

# Objective
1	Regional Sales Performance & Geographic Market Analysis
	>> Evaluate total revenue, transaction volume, and average order value across different geographic regions (Region) to identify high-performing markets and underperforming zones.
	
2	Impact of Discount Strategies on Net Revenue and Volume
	>> Investigate the relationship between Discount percentages and the resulting Quantity sold versus total net Sales to determine whether discounting successfully stimulates demand or negatively impacts revenue margins.
	
3	Product Demand and Revenue Concentration Analysis
	>> Identify which specific Product lines dominate total revenue generation and sales volume to pinpoint core revenue drivers versus low-performing inventory
	
4	Evaluate Customer Value and Profitability
	>> Identify high-value, medium-value, and low value customers by analysing revenue contribution and customer lifetime value, helping the company focus retention efforts on profitable customers. 
	
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
columns_to_convert = ['order_date', 'shipping_date']
for col in columns_to_convert:
    df[col] = pd.to_datetime(df[col], format='%d-%m-%Y')

# Quick view of top 5 data info
df.head()


## Key Findings
Objective 1:
1. There is no customer concentration risk
Customer spending appears to be relatively evenly distributed among the leading customers, with no clear indication of excessive reliance on a single customer. This suggests that revenue is supported by a broader customer base, reducing customer concentration risk.

2. Sales volume does not represent high revenue
Some product categories, including Sports Shoes, Activewear Sets, Jackets and T-Shirts, recorded relatively strong sales volumes but remained among the lower revenue contributors. This indicates that high transaction volume alone does not guarantee strong revenue performance. Product pricing, discounts and product mix may contribute to this difference.

The analysis shows differences in performance across product categories. Certain categories contribute more strongly to revenue, while others generate comparatively lower revenue despite higher customer demand. This highlights the importance of assessing both sales quantity and revenue contribution when evaluating product performance.



