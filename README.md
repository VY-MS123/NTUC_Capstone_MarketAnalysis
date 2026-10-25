# NTUC_Capstone_MarketAnalysis (prepared by Yep We Ping)
Retail Customer Purchase Analytics

# Product Sales Dataset 📊

<p align="center">
<img width="896" height="373" alt="image" src="https://github.com/user-attachments/assets/aea94c68-9d7e-48b4-af7a-e12957d9d1d0" />

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

## Power BI Dashboard

<img width="1419" height="790" alt="image" src="https://github.com/user-attachments/assets/a32f26df-5002-43dc-9a84-57e5a0099a90" />

## 📋 Dataset Overview

* **File Name:** `customer.csv`
* **Target Category:** Customer Directory
* **Key Entities:** Customer ID,First Name, Last Name, Gender, Age, Country, Income

  <p align="center">
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

## Key Findings
Objective 1:
Sales volume does not represent high revenue
Some product categories, including Sports Shoes, Activewear Sets, Jackets and T-Shirts, recorded relatively strong sales volumes but remained among the lower revenue contributors. This indicates that high transaction volume alone does not guarantee strong revenue performance. Product pricing, discounts and product mix may contribute to this difference.

The analysis shows differences in performance across product categories. Certain categories contribute more strongly to revenue, while others generate comparatively lower revenue despite higher customer demand. This highlights the importance of assessing both sales quantity and revenue contribution when evaluating product performance.

Objective 2:
In normal promotion circumstances, discount can encourage purchases, but higher discounts do not necessarily mean better financial performance. The finding suggest that discounts have a limited impact on increasing customer demand. Therefore, discount effectiveness should be assessed together with sales volume, revenue and, where available, profitability to determine whether promotions are creating sufficient business value. 

Objective 3:
1. There is no customer concentration risk
Customer spending appears to be relatively evenly distributed among the leading customers, with no clear indication of excessive reliance on a single customer. This suggests that revenue is supported by a broader customer base, reducing customer concentration risk.

2. There is product concentration risk
The analysis shows a high level of product concentration, with 10 key products contributing 69% of the company’s total revenue. To manage this concentration risk, management should regularly monitor sales trends, inventory levels and profitability of these products. Consistent product quality and high customer satisfaction should also be maintained to protect demand and sustain revenue contribution.

Objective 4:
Customer purchasing behaviour provides opportunities for segmentation
Differences in customer spending patterns suggest opportunities to group customers according to their purchasing behaviour and value. Customer segmentation can help the business identify higher-value customers and develop more relevant marketing strategies rather than applying the same approach to all customers.

Based on the analysis, the 20–30 age group is the strongest revenue contributor, generating approximately $17 million, while customers aged 30–60 continue to provide a stable revenue base. Revenue declines significantly among customers above 60. Importantly, each age group shows different demand for top products, highlighting an opportunity to tailor product offerings and marketing strategies to specific age segments.

Objective 5:
Sales Trends and Demand Seasonality Analysis
The sales performance seem to be stable but the sales demand chart showing October is the peak of the year. Although November and December sales decrease slightly as compared to October, they remain significantly higher than the first half of the year. This suggests stronger customer demand in the third and fourth quarters, likely driven by seasonal shopping patterns and year-end promotional activities.

Based on this trend, the company should focus inventory planning and marketing campaigns during August to December, while leveraging weekend promotions to maximise sales opportunities.

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




