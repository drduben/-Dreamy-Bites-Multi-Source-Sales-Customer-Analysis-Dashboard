📌 Project Overview
	
Client	Dreamy Bites — a premium cookie brand selling Chocolate Chip, Oatmeal Raisin, Snickerdoodle, Sugar, Fortune, and White Chocolate Macadamia Nut cookies to retail partners
Role	Data Analyst
Tool Used	Power BI (Power Query for multi-source ingestion, relational data modeling, DAX measures)
Reporting Period	September 2019 – December 2020 (16 months)
Data Scope	700 orders across 5 retail customers and 6 cookie products
🎯 The Business Problem

Dreamy Bites' data lived in three completely disconnected places:

A PDF file containing product descriptions and updated selling prices
A CSV file storing customer information
A Google Sheet tracking orders — quantities, dates, and payment details

None of these sources talked to each other. That fragmentation made it impossible to answer basic strategic questions — which products were actually profitable, which customers mattered most, how sales trended over time — without manually cross-referencing three unrelated files.

🛠️ The Solution: Unifying Three Sources Into One Model

The core skill this project demonstrates is data integration, not just dashboarding. Each source fed into Power BI to become one connected data model:

Orders (from the Google Sheet) → became the fact table, Order_fact — 700 transaction rows, each with Customer ID, Order ID, Product, Units Sold, and Date
Customers (from the CSV) → became the Customers_Dim dimension table — customer name, phone, address, city, state, and country
Products (from the PDF) → became the Product_Dim dimension table — cookie type, selling cost per cookie, and production cost per cookie

These three tables were connected through relationships (Customer ID and Product) into a proper star schema, so a single fact table could be sliced by any customer or product attribute — turning three static files into one live, queryable model.

Core DAX Measures
DAX
Total Revenue    = SUM(Order_fact[Revenue])
Total Expenses   = SUM(Order_fact[Expenses])
Total Profit     = SUM(Order_fact[Profit])
Total Qty Sold   = SUM(Order_fact[Units Sold])
No of Customers  = DISTINCTCOUNT(Order_fact[Customer ID])
No of Products   = DISTINCTCOUNT(Order_fact[Product])
Total Orders     = DISTINCTCOUNT(Order_fact[Order ID])
Profit Margin    = DIVIDE([Total Profit], [Total Revenue])

Revenue, Expenses, and Profit are calculated at the transaction level from each product's selling and production cost — meaning every KPI on the dashboard is driven dynamically from the underlying cost structure, not hardcoded.

📊 The Dashboard

The report is built as two linked pages — Customer Analysis and Product Analysis — sharing the same underlying model and a Product filter.

Headline KPIs
Metric	Value
Total Revenue	$4,690,319
Total Expenses	$1.97M
Total Profit	$2.72M
Total Orders	700
Total Quantity Sold	1.13M units
Profit Margin	58%
No. of Customers	5
No. of Products	6
Customer Analysis page
Profit Target gauge — $2.72M actual vs. a $3M target (91% of goal)
Quantity Sold Target gauge — 1,125,824 units vs. a 2M target (56% of goal)
Profit by State (map) — Wisconsin, New York, Utah, Alabama, Washington
Profit & Total Expenses by Customer (bar chart)
Orders by Customer and Quantity Sold by Customer (bar charts)
Product Analysis page
Profit and Total Quantity Sold by Year and Month (combo line/area chart) — full 16-month trend
Profit and Total Expenses by Product (bar chart)
Orders by Product and Quantity Sold by Product (bar charts)
✅ Key Business Questions — Answered
Question	Answer
Which customer is the most valuable?	ACME Bites (Wisconsin) leads by a wide margin — $828,388 profit from 206 orders and 330K units — nearly 30% more profit than the next-highest customer
How does profit rank across all 5 customers?	ACME Bites ($828K) > Wholesome Foods ($640K, New York) > ABC Groceries ($523K, Utah) > Park & Shop Convenience Stores ($424K, Alabama) > Tres Delicious ($302K, Washington)
Which product drives the most profit?	Chocolate Chip dominates at $1,014,729 — more than double the next-best product — from 338K units sold across 202 orders
How does profit rank across all 6 products?	Chocolate Chip ($1.01M) > White Chocolate Macadamia Nut ($528K) > Oatmeal Raisin ($435K) > Snickerdoodle ($367K) > Sugar ($295K) > Fortune Cookie ($77K)
Which product has the best profit margin per unit?	Snickerdoodle — a 62.5% margin per cookie ($4 selling price vs. $1.50 production cost) — actually the highest of any product, even though it isn't the top total profit earner
How has profit trended over the 16-month period?	Profit shows a recurring cyclical pattern rather than a steady trend, with pronounced peaks roughly every quarter — $223K in October 2019, $247K in June 2020, and $252K in October 2020 — separated by troughs in the $124K–$139K range, suggesting periodic bulk reordering rather than smooth month-to-month demand
Is the business on track against its targets?	Profit is close to target ($2.72M of $3M, 91%), but volume is well behind target (1.13M of 2M units, only 56%) — the business is hitting close to its profit goal despite falling well short on unit volume, implying pricing/margin is doing more work than volume growth
🔍 Key Insights
Customer concentration is significant: with only 5 retail customers, ACME Bites alone drives nearly a third of total company profit ($828K of $2.72M) — a single-customer dependency worth monitoring closely.
Chocolate Chip is the clear flagship product, generating more profit than the next two products combined, and leading every metric — orders, quantity sold, and profit.
Fortune Cookie is a clear underperformer: lowest profit ($77K), lowest revenue, and the lowest per-unit margin (50%) of any product — despite reasonably competitive unit volume (154K units), it contributes the least value per cookie sold.
Margin and volume tell different stories: Snickerdoodle has the best per-unit margin (62.5%) but ranks only 4th in total profit, because Chocolate Chip's much higher volume more than compensates for its slightly lower margin (60%) — a classic volume-vs-margin trade-off.
The business is on pace for profit but not for volume: sitting at 91% of its profit target but only 56% of its unit-volume target suggests pricing or product mix is stronger than raw sales growth — worth understanding whether that's a deliberate premium strategy or a demand shortfall.
Demand is cyclical, not steady: the roughly quarterly peak-and-trough pattern in the monthly trend chart looks more like periodic bulk restocking by retail partners than organic, steadily growing consumer demand — useful for production and inventory planning.
💡 Recommendations
Reduce reliance on ACME Bites by actively growing the other four accounts, given how much of total profit sits with a single customer.
Investigate Fortune Cookie's future in the lineup — its low margin and low profit contribution make it a candidate for repricing or discontinuation.
Study Snickerdoodle's pricing model as a potential template for improving margins on other products, given it already delivers the best per-unit profitability.
Align production planning to the quarterly demand cycle identified in the trend chart, rather than assuming flat monthly demand.
Dig into the volume shortfall against the 2M-unit target — determine whether it reflects a deliberate premium-pricing strategy or an unmet growth opportunity worth pursuing.
🛠️ Skills Demonstrated

Power BI · Multi-Source Data Integration · Power Query · Star-Schema Data Modeling · DAX Measures · KPI & Target Tracking · Geospatial Visualization · Wholesale/FMCG Analytics · Business Insight Generation

📁 Repository Contents
Dreamy_Bites_Workspace.pbix — full Power BI file (integrated data model, DAX measures, both report pages)
Dreamy_Bites_Product_Dashboard.png — Product Analysis report page
Dreamy_Bites_Customer_Dashboard.png — Customer Analysis report page
Dreamy_Bites_Case_Study_Brief.docx — original project brief
README.md — this write-up

Case study based on the Dreamy Bites project brief. #PowerBI #DataAnalytics #DAX #DataIntegration
Add case study write-up and dashboard screenshot
