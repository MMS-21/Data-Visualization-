
## Plant Co. Sales Performance 2023 – Power BI Report

### 1. **Overview**
This Power BI report visualizes the year-to-date (YTD) sales performance for Plant Co. in 2023. The report tracks key metrics like sales, gross profit percentage (GP%), and prior year-to-date (PYTD) sales. Custom measures, such as **Gross Profit**, **Revenue**, and **PYTD**, were calculated to enhance insights and comparisons. The report provides a detailed look into the performance of different countries, product categories, and time periods.

### 2. **Data Source**
The dataset is sourced from [Kaggle](https://www.kaggle.com), originally lacking the gross profit and revenue fields. These fields were calculated using custom DAX measures in Power BI:
- **Gross Profit**: Calculated as the difference between **Revenue** and **Cost**.
- **Revenue**: Derived from the sales data, representing the total income from product sales.

### 3. **Key Metrics**
 - **YTD Sales:** Total sales generated from January 1st to the current date.
 - **YTD vs PYTD:** Percentage difference between YTD sales in 2023 and 2022.
 - **Gross Profit:** Total revenue minus the cost of goods sold.
 - **GP%:** Gross profit percentage calculated as (Gross Profit / YTD Sales) * 100.
#### Top 10 YTD vs PYTD by Country
 - **Country:** Countries ranked based on their YTD sales performance compared to the previous year.
 - **Sales YTD vs PYTD:** Percentage increase or decrease in YTD sales for each country.
 - **Increase/Decrease:** Indicates whether a country's sales have increased or decreased compared to the previous year.
#### Sales YTD & PYTD by Month
 - **Month:** Monthly breakdown of YTD sales for 2023 and 2022.
 - **Sales:** Total sales for each month.
 - **Product Type:** Breakdown of sales by product type (Indoor, Landscape, Outdoor).
#### Account Profitability Segmentation
 - **GP% and (Sales, Quabtity or Gross Profit):** Scatter plot visualizing the relationship between gross profit percentage and sales for different accounts.
 - **Value YTD:** Total sales for each account.

----
![Whole view](https://github.com/MMS-21/Data-Visualization-/blob/0a7fcdf7159f111f0a84e9a6f27a47eefa266ddc/Power%20BI%20Dashboard%20Plant%20Co.%20Performance%202022%20-%20204/QuickShots/Whole%20Dashboard.png)
----

### 4. **Visual Breakdown**
- **Top 10 YTD vs PYTD by Country**: A tree map showcasing the top 10 countries by sales, comparing their YTD performance against PYTD. Custom measures for each country track their YTD and PYTD sales. For example, **Portugal** leads with **179.22K** in sales.
----
![Tree Map](https://github.com/MMS-21/Data-Visualization-/blob/0a7fcdf7159f111f0a84e9a6f27a47eefa266ddc/Power%20BI%20Dashboard%20Plant%20Co.%20Performance%202022%20-%20204/QuickShots/CatMap.png)
----
- **(Sales, Quabtity or Gross Profit) YTD & PYTD by Month-Country-Product**: A waterfall chart where each bar represents the variance in sales between YTD and PYTD for each month. This visual uses the custom **PYTD** measure to show how sales changed month over month.
----
![Waterfall Chart](https://github.com/MMS-21/Data-Visualization-/blob/0a7fcdf7159f111f0a84e9a6f27a47eefa266ddc/Power%20BI%20Dashboard%20Plant%20Co.%20Performance%202022%20-%20204/QuickShots/Waterfall.png)
----
- **(Sales, Quabtity or Gross Profit) YTD vs PYTD by Product Type (Monthly)**: A stacked bar chart displaying YTD and PYTD values across product categories (Indoor, Landscape, Outdoor). The **PYTD** measure enables a month-by-month comparison.
----
![Stacked Bar Chart](https://github.com/MMS-21/Data-Visualization-/blob/0a7fcdf7159f111f0a84e9a6f27a47eefa266ddc/Power%20BI%20Dashboard%20Plant%20Co.%20Performance%202022%20-%20204/QuickShots/Barchart.png)
----
- **Account Profitability Segmentation (GP% and Sales)**: A scatter plot showing the custom **Gross Profit** measure against sales values, allowing for quick identification of profitable accounts and those that need improvement.
----
![Scatter Plot](https://github.com/MMS-21/Data-Visualization-/blob/0a7fcdf7159f111f0a84e9a6f27a47eefa266ddc/Power%20BI%20Dashboard%20Plant%20Co.%20Performance%202022%20-%20204/QuickShots/Scatter.png)
----
### 5. **Filters and Slicers**
- **Year To Date Filter**: Allows users to switch between different years, with YTD and PYTD measures dynamically updating based on the selected year.
- **Metric Filter**: Users can toggle between different performance metrics, such as **Gross Profit**, **Quantity**, and **Sales**, providing a multi-dimensional analysis.

### 6. **User Guide**
- Select the **Year To Date** slicer to change between 2022, 2023, or 2024, and observe how the custom YTD and PYTD measures adjust to reflect sales trends.
- Use the **Metric Filter** to analyze different metrics like **Gross Profit** and **Sales**, **Quantity** throughout the year.
- Hover over charts for additional details on YTD vs PYTD performance.

### 7. **Custom DAX Measures**
The following custom DAX measures were created to facilitate more advanced analysis:
#### Base Measures:
- **GP%**: `GP% = DIVIDE([Gross Profit],[Sales])`
- **Gross Profit**: `Gross Profit = [Sales] - [COGs] `
- **Quantity**: `Quantity = SUM(Fact_sales[quantity]) `
- **Sales**: `Sales = SUM(Fact_sales[Sales_USD])`
 #### Prior Year To Date:
- **PYTD Gross Profit**: `PYTD_GrossProfit = CALCULATE(
    [Gross Profit],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE
)`
- **PYTD Quantity**: `PYTD_Quantity = CALCULATE(
    [Quantity],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE
)`
- **PYTD Sales**: `PYTD_Sales = CALCULATE(
    [Sales],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE
)`
#### YTD:
- **YTD Gross Profit**: `YTD_GrossProfit = 
    TOTALYTD(
        [Gross Profit],
         Fact_sales[Date_Time]
    )`
- **YTD Quantity**: `YTD_Quantity = TOTALYTD([Quantity], 
             Fact_sales[Date_Time]
  )`
- **YTD Sales**: `YTD_Sales = TOTALYTD([Sales],
   Fact_sales[Date_Time]
  )`

### 8. **Insights from the Report**
- Despite the decline in overall YTD sales compared to PYTD, **Portugal** and **Philippines** continue to perform well.
- **Gross Profit** remains healthy, with a strong **GP%** of **39.62%**, indicating good profitability across the product lines.
- The **Account Profitability Segmentation** highlights key accounts that contribute heavily to profits, helping to focus on high-value customers.

### 9. **Recommendations for Plant Co. Based on the Dashboard**

#### Sales Performance:
- **Focus on Top-Performing Countries**: Prioritize sales efforts in countries like Portugal and the Philippines, which have shown significant year-over-year growth.
- **Address Underperforming Regions**: Investigate the reasons for declining sales in countries like Colombia and Germany. Consider implementing targeted strategies to improve performance in these areas.
- **Optimize Product Mix**: Analyze the sales performance of different product types to identify opportunities for optimization. For example, if outdoor products are underperforming, consider adjusting pricing, marketing, or product offerings.
#### Sales Strategy:
- **Diversify Sales Channels**: Explore opportunities to expand sales channels beyond the current ones, such as e-commerce or partnerships with distributors.
- **Enhance Customer Experience**: Focus on improving customer satisfaction through excellent service, personalized recommendations, and efficient order fulfillment.
- **Leverage Data Analytics**: Utilize data analytics to identify customer trends, preferences, and buying patterns. This information can be used to tailor marketing efforts and improve sales effectiveness.
#### Operational Efficiency:
- **Optimize Supply Chain**: Review the supply chain process to identify areas for improvement, such as reducing lead times, minimizing inventory costs, and improving transportation efficiency.
- **Enhance Production Capacity**: Assess production capacity to ensure it can meet increasing demand. If necessary, invest in additional equipment or facilities to expand production capabilities.
- **Improve Cost Management**: Implement cost-saving measures to improve profitability, such as negotiating better deals with suppliers, reducing waste, and optimizing resource utilization.
#### Marketing and Sales:
- **Targeted Marketing Campaigns**: Develop targeted marketing campaigns based on customer segmentation and preferences. Utilize digital marketing channels to reach your target audience effectively.
- **Salesforce Training**: Provide sales teams with ongoing training and development to equip them with the skills and knowledge needed to succeed in today's competitive market.
- **Customer Relationship Management (CRM)**: Implement a CRM system to track customer interactions, manage sales pipelines, and improve customer retention.
-------
**By addressing these areas, Plant Co. can enhance its sales performance, improve operational efficiency, and achieve sustainable growth.**
-------
