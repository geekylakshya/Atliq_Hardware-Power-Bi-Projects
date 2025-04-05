# Power BI Sales Analysis Project – Atliq Hardware

## Problem Statement

Atliq Hardware is a brand that supplies computer peripheral devices and hardware to clients across India. The company is currently facing several challenges due to a rapidly growing and dynamic market environment. One of the key issues is a decline in sales performance, and the leadership team lacks actionable insights into the business.

Atliq Hardware operates offices across multiple regions in India — including North, South, and Central zones. Currently, when the Sales Director needs sales insights from these regions, they must contact the respective Regional Managers directly. This communication is entirely verbal, making it difficult to verify the accuracy of the information provided. There are concerns about whether the Regional Managers are being fully transparent.

In addition, many repetitive and time-consuming tasks are performed manually, such as exporting Excel reports or running complex SQL queries. This adds inefficiency and delays to the decision-making process.

To address these challenges, the Sales Director requested a Power BI dashboard that provides real-time, reliable, and visual insights into sales performance. This solution aims to improve transparency, reduce manual workload, and support smarter business decisions.

---
## AIMS GRID  
![AIMS GRID](https://github.com/geeklakshya/project-img/blob/fdc7f3117e18df8962228186077e8a96831416f0/AIMS%20GRID.png)

## Steps Followed

### Step 1: Load Data
- Loaded data into Power BI Desktop.
- Data was imported directly from a MySQL database.

### Step 2: Transform Data
- Clicked on **"Transform Data"** to open Power Query Editor.
- Cleaned and shaped the data to prepare it for visualization.

### Step 3: Clean Sales Market Table
- In the `sales_market` table, removed rows with null values in the **zone** column (only two rows affected).

### Step 4: Normalize Currency in Transactions
- In the `sales_transaction` table, identified two transactions in **USD** instead of **INR**.
- Added a new column called `normalized_sales_amount`.
- Converted USD to INR using a DAX formula and updated the new column accordingly.
- For existing INR transactions, the original values were copied into the new column.

### Step 5: Remove Invalid Transactions
- Filtered out transactions where `sales_amount` was zero or negative, as they have no analytical value.

### Step 6: Apply Additional Transformations
- Identified and corrected any remaining data inconsistencies.
- Applied all transformations to finalize the cleaned dataset.

### Step 7: Data Modeling
- Established relationships between the tables to build a valid data model.
- Followed a **Star Schema** structure consisting of:
  - **Fact Table**: `sales transaction`
  - **Dimension Tables**: `sales products`, `sales customers`, `sales markets`, `sales date`, etc.

#### Data Model Structure
![Data Model](https://github.com/geeklakshya/project-img/blob/87698790daa2f67981de27c63b1d7bee953b6d3b/data%20model.png)

### Step 8: Dashboard Creation
- Built interactive dashboards in Power BI based on the Sales Director's business requirements.
- Dashboards provide a clear overview of sales performance, profitability, and customer/product trends to help stakeholders make informed decisions.

### Key Dashboard Metrics & Visuals

### Time-Based Analysis
- Year and Month-wise Total Revenue
- Year and Month-wise Total Sales Quantity
- Year and Month-wise Total Profit Margin
- Monthly Trends in Sales and Profit Contribution
- Profit Margin Trend Over Time

### Market & Regional Insights
- Revenue by Market
- Sales Quantity by Market
- Market-wise Profit Percentage
- Market-wise Profit Contribution %
- Market-wise Revenue Contribution %
- Sales Performance by Region

### Performance & Profitability
- Profit Margin Analysis
- Target vs Actual Profit Metrics

### Top Contributors
- Top 5 Customers by Revenue
- Top 5 Products by Revenue

## Dashboard Preview

## Key Insights
![Key Insights](https://github.com/geeklakshya/project-img/blob/6c338d808bd8a0a6029c85ffd98910777f9631ea/key%20insights.gif)

## Profit Margin Analysis
![Profit Margin](https://github.com/geeklakshya/project-img/blob/5974d5189ded5e9b924bbd61b562e6f62dbb6d4a/profit%20margin%20analysis.gif)

## Performance Insights
![Performance Insights](https://github.com/geeklakshya/project-img/blob/e7983f6356fc7934e43e33441c8ab278f31b111e/Performance%20Insights.gif)
