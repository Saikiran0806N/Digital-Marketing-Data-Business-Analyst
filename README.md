
# SALES ANALYSIS DASHBOARD 


### 1. Problem statement

Sales Performance & Profitability Optimization
Businesses generate sales across multiple products, customers, cities, and promotional campaigns, but total revenue alone does not explain whether sales performance is profitable or sustainable.

The objective of this project is to analyze transactional sales data using Power BI to identify sales trends, evaluate profitability, understand the contribution of promotions, compare geographic performance, and identify the best- and worst-performing products.

The analysis aims to help business stakeholders make data-driven decisions regarding product assortment, promotional investments, inventory prioritization, and sales growth opportunities.

Business questions your dashboard should answer
- Sales performance: How are net sales changing over time?
- Profitability: Which products or sales segments generate the most profit?
- Promotions: Which promotions are associated with higher discounted sales, and are they worth the discount offered?
- Geographic performance: Which cities contribute most to sales and profit?
- Product performance: Which products rank in the top and bottom five for sales, units sold, and profit?
- Period comparison: How do sales, profit, and quantities differ between two selected time periods?
- Customer contribution: Which customers contribute significantly to sales, and where are there opportunities to improve customer value?

### 2. Project roadmap: From raw data to business recommendations

Step 1 — Data understanding and preparation

Objective: Establish a reliable foundation for analysis.
- Identify transaction-level records, date fields, customers, products, cities and promotions.
- Check missing values, duplicates, data types and inconsistent records.
- Validate sales, profit, discounts and quantity calculations.
- Confirm the grain of the fact table, such as one row per order line.
  
  Deliverable: Clean, validated dataset.




Step 2 — Data modeling and relationships

Objective: Build a model that supports accurate analysis.
- Connect the sales fact table with customer, product and promotion dimensions.
- Establish a proper calendar table and date relationships.
- Validate one-to-many relationships and filter direction.
- Create reusable DAX measures for sales, profit, quantity and profitability.
  
  Deliverable: A reliable Power BI semantic model.




Step 3 — Exploratory sales analysis

Objective: Understand what drives business performance.
- Track net sales and profit trends.
- Compare sales and units sold by product.
- Examine city-level sales and profit distribution.
- Evaluate discounted sales by promotion.
  
  Deliverable: Performance patterns and areas requiring investigation.




Step 4 — Advanced analysis

Objective: Move beyond descriptive reporting.
- Rank the top and bottom five products by sales, profit and units.
- Compare two periods using date slicers.
- Calculate profit margin and sales growth.
- Investigate whether discounts coincide with higher volume or weaker margins.
  
  Deliverable: Prioritized opportunities and potential risks.




Step 5 — Recommendations and business action

Objective: Translate findings into decisions.
- Prioritize profitable products and investigate loss-making products.
- Review promotion effectiveness and discount policies.
- Identify cities with growth potential.
- Recommend performance monitoring through recurring reports.
  
  Deliverable: An actionable business review for stakeholders.



### 3. Dashboard map

Page 1 — Overview / Sales Trend
Performance overview
- Explain the overall sales trajectory.
- Compare net sales across years or periods.
- Examine the relationship between sales and profit.
- Review discounted sales by promotion.
Business takeaway: Are sales growing, and is profitability moving in the same direction?

Page 2 — Sales by City
Geographic performance
- Compare net sales across cities.
- Examine total profit by geography.
- Identify high-contribution and low-contribution locations.
Business takeaway: Where should the business protect its existing performance or investigate opportunities for expansion?


Page 3 — Top / Bottom 5 Analysis
Product optimization
- Rank products by net sales.
- Identify products with high and low units sold.
- Compare product profitability.
- Look for high-sales, low-profit products.
Business takeaway: Which products should receive more attention, and which require pricing, cost or assortment reviews?



Page 4 — Sales, Profit and Quantity Across Two Dates
Period comparison
- Compare sales between selected periods.
- Compare quantities sold and profit.
- Investigate whether changes in volume explain changes in sales.
Business takeaway: Is the business improving over time, and what metric is driving the change?



Page 5 — Transaction Detail and Filters
Drill-down analysis
- Filter by customer, product, promotion and date.
- Inspect transaction-level values.
- Validate summary findings against underlying records.
Business takeaway: Can a stakeholder trace a KPI to the relevant customer, product or transaction?

### 4. Key insights to showcase

I could inspect the PBIX report structure and visual fields, but I have not verified its underlying transaction values. Therefore, the following are insight hypotheses to test, not confirmed findings. Add the actual values from your dashboard before presenting them as results.

Insight 1 — Revenue growth versus profitability
Where to look: Overview / Sales Trend

Question: Are sales and profit increasing together?
- Calculate the percentage change in sales and profit between comparable periods.
- Track profit margin to determine whether growth is translating into stronger profitability.
- Investigate periods where sales rise but profit margin falls.
Potential action: Review cost structure, product mix and discounting during periods of weaker margin.

Insight 2 — Product concentration and underperformance
Where to look: Top / Bottom 5 Analysis

Question: Are a small number of products driving most of the business results?
- Compare top-five and bottom-five products across sales, profit and quantity.
- Identify products with strong sales but weak profit.
- Check whether low sales reflect low demand, limited availability or pricing issues.
Potential action: Prioritize profitable products while investigating underperformers before changing inventory or assortment.

Insight 3 — Promotion effectiveness
Where to look: Overview / Sales Trend

Question: Do promotions generate enough incremental value to justify the discount?
- Compare discounted sales, units sold and profit across promotions.
- Measure average discount and profit margin.
- If a baseline is available, compare promotional results with a comparable non-promotional period.
Potential action: Retain or expand promotions only when their incremental contribution justifies their cost. Discounted sales alone do not prove promotion effectiveness.

Insight 4 — Geographic opportunity
Where to look: Sales by City

Question: Which cities generate sales efficiently, and where is performance weak?
- Rank cities by sales and profit.
- Compare profit margins across cities.
- Identify high-sales cities with low profitability and low-sales cities with potential for improvement.
Potential action: Investigate local pricing, product mix, customer demand and operating costs before reallocating resources.

Insight 5 — Sales volume versus value
Where to look: Two-Date Comparison

Question: Is performance changing because of quantity sold, realized sales value or profitability?
- Compare units sold, net sales and profit across the same two periods.
- Calculate average net sales per unit, where appropriate.
- Determine whether volume growth coincides with margin improvement.
Potential action: Focus on the factors driving profitable growth rather than sales volume alone.

### 5. KPIs and DAX measures 

KPI	Calculation	Why it matters
Net Sales	SUM(Fact[Net Sales])	Measures sales value
Total Profit	SUM(Fact[Profit])	Measures absolute profit
Units Sold	SUM(Fact[Units Sold])	Measures sales volume
Profit Margin %	Profit ÷ Net Sales	Measures profitability relative to sales
Average Discount %	Average of discount percentage	Measures typical discount level
Sales Growth %	(Current − Previous) ÷ Previous	Measures sales change over time
Average Sales per Unit	Net Sales ÷ Units Sold	Tracks realized value per unit



Example DAX measures:
Total Sales =
SUM('Fact Table'[Net Sales])

Total Profit =
SUM('Fact Table'[Profit])

Total Units =
SUM('Fact Table'[Units Sold])

Profit Margin % =
DIVIDE([Total Profit], [Total Sales], 0)

Average Sales per Unit =
DIVIDE([Total Sales], [Total Units], 0)


For time-based comparisons, create a proper calendar table, mark it as the date table and use the correct active relationship to the sales date.
Previous Period Sales =
CALCULATE(
    [Total Sales],
    DATEADD('Calendar'[Date], -1, MONTH)
)

Sales Growth % =
DIVIDE(
    [Total Sales] - [Previous Period Sales],
    [Previous Period Sales]
)


This example calculates month-over-month change when the visual is evaluated at a monthly grain. For year-over-year comparisons, use a one-year date shift instead.
