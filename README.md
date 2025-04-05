# Power BI Project: Sales Insights – AtliQ Hardware


## Table of Contents
- [Problem Statement](#problem-statement)
- [Data Discovery](#data-discovery)
- [Data Cleaning and ETL](#data-cleaning-and-etl)
- [Data Modeling](#data-modeling)
- [DAX Measures](#dax-measures)
- [Dashboard & Insights](#dashboard--insights)

---

## Problem Statement

Atliq Hardware is a brand that supplies computer peripheral devices and hardware to clients across India. The company is currently facing several challenges due to a rapidly growing and dynamic market environment. One of the key issues is a decline in sales performance, and the leadership team lacks actionable insights into the business.

Atliq Hardware operates offices across multiple regions in India — including **North, South, and Central zones**. Currently, when the Sales Director needs sales insights from these regions, they must contact the respective Regional Managers directly. This communication is entirely verbal, making it difficult to verify the accuracy of the information provided. There are concerns about whether the Regional Managers are being fully transparent.

In addition, many repetitive and time-consuming tasks are performed manually, such as exporting Excel reports or running complex SQL queries. This adds inefficiency and delays to the decision-making process.

To address these challenges, the Sales Director requested a Power BI dashboard that provides real-time, reliable, and visual insights into sales performance. This solution aims to improve transparency, reduce manual workload, and support smarter business decisions.

---

## Data Discovery

<table>
  <tr>
    <th> AIMS GRID</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/fdc7f3117e18df8962228186077e8a96831416f0/AIMS%20GRID.png" width="100%">
    </td>
  </tr>
</table>


<table>
  <tr>
    <th> PROJECT FLOW</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/a843fd0137c9daf3fd55da71dc8cfa289b6163ad/project%20flow.png" width="100%">
    </td>
  </tr>
</table>


---

## Data Cleaning and ETL

- Data was imported from a **MySQL** database into **Power BI Desktop**
- Opened **Power Query Editor** for ETL (Extract, Transform, Load)

### Key Cleaning Steps:

1. **Removed null values** from `zone` column in `sales market` table  
2. **Filtered out invalid transactions** (zero or negative sales amount)  
3. **Normalized currency**:  
   - Added `normalized_sales_amount` column  
   - Converted USD to INR using a conditional formula:  
     ```DAX
     norm_sales_amount = IF(currency = "USD", sales_amount * 85.6, sales_amount)
     ```

---

## Data Modeling

- Designed a **Star Schema** for optimal performance and usability

| Table Type     | Tables Used |
|----------------|-------------|
| **Fact Table** | `sales_transactions` |
| **Dimension Tables** | `sales_products`, `sales_customers`, `sales_markets`, `sales_date` |

### Final Data Model:

<table>
  <tr>
    <th> DATA MODEL</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/87698790daa2f67981de27c63b1d7bee953b6d3b/data%20model.png" width="100%">
    </td>
  </tr>
</table>

---

## DAX Measures

### Key Measures:

- **Total Revenue**
  ```DAX
  Revenue = SUM('sales transactions'[normalized_sales_amount])

- **Sales Quantity**
  ```DAX
  Sales Quantity = SUM('sales transactions'[sales_qty])

- **Total Profit Margin**
  ```DAX
  Total Profit Margin = SUM('sales transactions'[Profit_Margin])

- **Profit Margin %**
  ```DAX
  Profit Margin % = DIVIDE([Total Profit Margin], [Revenue], 0)

- **Revenue Contribution %**
   ```DAX
   Revenue Contribution % = 
   DIVIDE(
      [Revenue],
      CALCULATE([Revenue], 
        ALL('sales customers'),
        ALL('sales markets'),
        ALL('sales products')
    )
  )


- **Profit Margin Contribution %**
  ```DAX
    Profit Margin Contribution % = 
    DIVIDE(
        [Total Profit Margin],
        CALCULATE([Total Profit Margin], 
         ALL('sales customers'),
         ALL('sales markets'),
         ALL('sales products')
    )
  )

---
## Dashboard & Insights

Interactive dashboards were created based on the Sales Director's requirements to support strategic decisions.

<table>
  <tr>
    <th> Key Insights</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/6c338d808bd8a0a6029c85ffd98910777f9631ea/key%20insights.gif" width="100%">
    </td>
  </tr>
</table>

<table>
  <tr>
    <th> Profit Margin Analysis</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/5974d5189ded5e9b924bbd61b562e6f62dbb6d4a/profit%20margin%20analysis.gif" width="100%">
    </td>
  </tr>
</table>

<table>
  <tr>
    <th> Performance Overview</th>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/geeklakshya/project-img/blob/e7983f6356fc7934e43e33441c8ab278f31b111e/Performance%20Insights.gif" width="100%">
    </td>
  </tr>
</table>

