# Sales Insights Data Analysis- Power BI Dashboard

### Dashboard Link : 

## Problem Statement
The challenge at hand revolves around the need for a structured and insightful approach to leverage sales data for predicting market profit, contribution, and identifying key improvement areas. The current state of affairs involves disparate datasets containing crucial information about transactions, customer behavior, products, and market dynamics. The absence of a consolidated and analytically-driven framework inhibits the organization's ability to make informed strategic decisions.

### Key Issues:

#### Data Fragmentation:

* Sales data is scattered across various sources, making it difficult to establish a unified view of the business landscape.

#### Limited Predictive Capabilities:

* The absence of predictive analytics tools prevents the organization from foreseeing market trends, profit potential, and areas for improvement.

#### Strategic Decision-Making Hurdles:

* Without a dedicated analytical tool, the organization lacks the means to make strategic decisions based on comprehensive market insights.

### Objectives
The primary objectives of the Sales Dashboard Creation project are:

#### Unified Data Integration:

* Employ Power BI to perform ETL operations, ensuring seamless integration of diverse sales data sources for a comprehensive view.

#### Predictive Analytics Implementation:

* Leverage Power BI's capabilities to implement predictive analytics, enabling the organization to forecast market profit, contribution, and identify growth opportunities.

#### Enhanced Business Understanding:

* Develop a user-friendly and visually impactful dashboard that provides insightful data on market trends, customer behavior, and product performance.

#### Strategic Decision Empowerment:

* Facilitate strategic decision-making by presenting actionable insights through the Power BI dashboard, aiding in the identification of profitable zones and areas for business improvement.

* By achieving these objectives, the organization aims to transform raw sales data into a strategic asset, fostering a deeper understanding of market dynamics and enabling proactive decision-making for sustained business growth.


### Steps followed 

- Step 1 : 
i. Load data into Power BI Desktop, dataset is a .sql file. 

![Snap_1](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/bef0b66a-caf5-495d-b7b1-7b101d10e976)


ii. Making Use of Select the Database option from 'GET Data' menu and obtain data in the Power BI Dashboard by connecting to a MySQL database.

iii. Load all the datas from MySql

Note: Import the.sql file into MySql Workbench and examine the datasets to verify the data.

- Step 2 : Open power query editor & in view tab under Data preview section, check "Visualization", "Tables" & "Data Modelling" options.

- Step 3 : 'Data Modelling' by default shows you some relationships between the datas, established on its own. For few model have to do it manually by drag and drop options and establish the relationship connections with the tables. This action is also known as "Star Schema". It provides the Fact Table (Actual transaction, Events) and Dimension Table (Customer, Product, Market and so on)

![Snap_1](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/47d8db0d-5e4b-4983-aa81-83c10bd66373)

- Step 4 : Click Transform Data -> Power Query editor.

![Snap_1](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/4bdc6493-a55e-4d95-9dcc-17c8d734b495)


#### Data Cleaning:

- Step 5: Use the Power Query Editor's drop down filter option to remove the Blank values for "Newyork" and "Paris" from the Sales markets table. Additionally, you can review the procedure in the "APPLIED STEPS" field on the right.

- Step 6: In the Sales_Transaction table, a second ETL (Extract Transfrom and Load) has occurred. Using "Conditional Column" to convert USD values to INR, and then "convrt_sales_column" to multiply the USD value by Rs. 80 using the code below



           
           = Table.AddColumn(#"Filtered Rows", "convrt_sales_amount", each if [currency] = "USD" then [sales_amount]*80 else [sales_amount] )

- Step 7: After applying all modifications and go to 'Home' and select 'Close & Apply'. After loading, the visualization will reappear. The transformed data and filters can be viewed in the 'Tables' section.

Data Visualization:

- Step 8: Click "Enter Data" from HOME and create 'Base Measure'. Then,

First create New Measure for 'Revenue' use the Code below

           
           Revenue = SUM('sales transactions'[sales_amount])


Second create New Measure for 'Sales_Qty' use the Code below

           
           Sales Qty = SUM('sales transactions'[sales_qty])

These two measures gives you the perfect visualization dimension for "REVENUE AND SALES_QUANTITY"

Step 9: Select "REVENUE" + "SALES QTY" and then Drag, Drop, and Align. Next, create the year and CY_Date columns using the Slicer visual.

NOTE: Year, CY_Date is associated with the relationship between Total Revenue and Sales Quantity. You will receive the outcome for each clickable year and CY_date.

Step 10: 

![Sales Insights Dashboard Page1](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/171dfc0e-49d6-42f1-a0d0-9608e06255dc)

i. Revenue by Customers: This gives you the total revenue for each customer, sliced down by Customer Name. which makes it easier to identify each customer's highest and lowest revenue so that improvements and unique activities can be offered.

ii. Comparably, sales quantity by the customer. Which helps in determining the precise sales for both the month and the year.

iii. Revenue By Zone (Pie Chart), Revenue by Cy_date (Graph), Top 5 Customers by Revenue (Horizontal Graph View), Top 5 Products by Revenue (Horizontal Graph View). We can now able to understand the yearly and monthly sales,revenue, and profit with customers, dates, products, markets, and zones as a result to all of the above projections.

Step 11:
Click View -> Mobile Layout to create the Mobile View Layout.
Drag and drop the required blocks into the responsive mobile design. which enables the CEO or manager to monitor the unique sales perspective and makes adjustments as needed at anytime.


![Mobile Layout](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/85366b6a-536c-4d6f-8c3b-15b914f72dc7)


Step 12: To understand more about the business profit and loss in the given datasets from the year 2017 to 2020, added 


![Sales Insights Dashboard Page2](https://github.com/rajeshxtreme6/Power-BI-Sales-Dashboard/assets/147930077/f25ce4ab-c892-45ff-8521-ace587c18f32)


1.  “Total Profit Margin” , 

Base Measures:

           
           Total Profit Margin = SUM('sales transactions'[profit_margin])

2. “Profit Margin in % by Markets” (Horizontal View)
Base Measures:


           
           Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)


3. “Revenue Trend”, (Graphical View using Revenue, Year and Sum of Profit Margin Percent) 
4. “Revenue by Customer Type (Pie Chart) - which shows the total revenue happens either in E-commerce or Brick & Mortar
5. “Tabular View” for Customer Name, Sum of Cost_Price, Revenue and Sum of Profit_Margin - where you can check the datas in ascending and descending order in a click.


In conclusion, the Sales Insights Data Analysis project tackles the challenge of fragmented sales data, utilizing Power BI to integrate, clean, and predict market profit and contribution. The project addresses the hurdles in strategic decision-making by providing a visually impactful dashboard. Through ETL operations, predictive analytics, and comprehensive data visualization, the organization gains a unified understanding of customer behavior, product performance, and market dynamics. The mobile-responsive design enhances accessibility, allowing real-time monitoring. The added focus on profit margins enriches the analysis, fostering a deeper understanding of business trends from 2017 to 2020. This project empowers proactive decision-making for sustained business growth.
