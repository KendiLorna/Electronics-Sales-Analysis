## Electronics-Sales-Analysis(2016-2021)

## Tool: Microsoft Power BI


### Project Overview
This project presents a comprehensive analysis of electronics sales data spanning from 2016 to 2021.
The interactive Power BI dashboard provides insights into revenue, profitability, customer behavior, product and store performance, and geographic distribution across multiple dimensions.

### Business Context
The analysis examines an electronics retail business operating across multiple countries with both physical stores and online presence.
The dashboard enables stakeholders to understand key business metrics and trends over a six-year period, including the impact of market changes in 2020-2021.

### Business Questions
1. Overall Performance (KPI Tracking)

What is our total revenue, profit, quantity sold, and customer count?

Are these KPIs growing or declining compared to targets?

2. Trends Over Time (Monthly Analysis)

How have revenue, profit, quantity, and customer count changed month by
month since 2020?

Are there seasonal patterns or months where performance consistently drops?

3. Year-over-Year (YoY) Comparison

How does performance in the current year compare to previous years?

What is the YoY growth/decline % for revenue, profit, and customers?

Are we recovering or still trending downward

4. Product Performance
Which products, categories, and subcategories are driving revenue and profit
growth?

Which ones are underperforming and contributing to the decline?

What are the top 10 best-sellers vs. the bottom 10 laggards?

Are our profit margins shrinking due to rising costs or discounting?

5. Customer Insights

Who are our customers? (gender, age, geography)

Are we losing existing customers or failing to attract new ones?

Which customer segments contribute the most to revenue and profit?

Are younger or older demographics shifting their buying behavior

6. Store & Regional Performance

Which stores, states, and countries are performing well vs. declining?

Are certain regions driving the overall revenue decline?

How does store performance vary based on open date (new vs. old stores)?

### Data Structure
The dataset includes the following key information:

-- Time Period: 2016-2021

-- Geographic Coverage: United States, United Kingdom, Germany, Canada, Australia, France, Italy, Netherlands, and Online sales

-- Product Categories: Computers, Home Appliances, Cameras and Camcorders, Cell Phones, TV and Video, Audio, Music/Movies/Audio Books, Games and Toys

-- Brands: 11 major brands including Adventure Works, Wide World Importers, Contoso, Fabrikam, and others

### Data Modelling
Used the star schema to model the data.

### Data Preparation
Calculated Measures Created
I developed several DAX measures to enable comprehensive analysis:

Total Revenue - Sum of all sales transactions
Total Profit - Revenue minus total costs
Total Cost - Sum of product costs
Quantity Sold - Count of units sold
Total Orders - Count of distinct orders
Year-over-Year Growth % - Percentage change metrics for revenue, profit, quantity, and costs
Profit Margin % - Profit as a percentage of revenue

Calculated Columns
Age Groups: Created a calculated column to segment customers into meaningful age brackets:
19-29
30-39
40-49
50-59
60-69
70-79
80+
Created a date table
This segmentation enables targeted analysis of customer preferences and purchasing behavior across different demographics.
Key Insights
Overall Performance

Total Revenue: $55.76M (up 1.9% YoY)
Total Profit: $32.66M (up 1.9% YoY)
Quantity Sold: 197.76K units (up 2.0% YoY)
Customer Base: 11.89K customers (up 0.6% YoY)
Total Orders: 62.88K (up 2.0% YoY)

Notable Trends

Seasonal Patterns: Significant revenue decline in March-April, with recovery beginning in May and stabilization through year-end
Customer Demographics:

Nearly balanced gender distribution (49% female, 51% male)
Peak customer concentration in 19-29 age group (1.82K customers)
Strong representation across middle-age groups (30-59)


Geographic Performance:

United States dominates with 5.71K customers
Strong European presence led by United Kingdom (1.57K customers)
Online channel generates $2.4M in revenue


Product Category Insights:

Computers lead in revenue and profit generation
Strong performance in Home Appliances category
Games and Toys show consistent demand across age groups


Brand Performance:

Adventure Works leads with $4.17M in revenue
Wide World Importers second at $1.81M
Top brands show strong profit margins


Business Trajectory:

Peak customer count in 2019 (6.50K)
Significant decline in 2020-2021, potentially due to market disruptions
2021 shows reduced operations with only 3,797 units sold


Store Operations:

Store longevity strongly correlates with revenue generation
Peak revenue achieved by stores operating 14-16 years
Continental performance shows varied YoY trends, with Europe experiencing the steepest decline (-91.0% in 2021)



Dashboard Features
The dashboard includes four main views:

Overview: High-level KPIs, monthly trends, and brand/country revenue distribution
Customers: Demographics, geographic distribution, age-based preferences, and customer trends
Products: Year-over-year performance, brand analysis, product category breakdown, and top/least popular products
Stores: Store profitability analysis, geographic distribution, and impact of operational longevity

Technical Implementation

Data Modeling: Star schema with fact and dimension tables
Visualizations: Mix of cards, line charts, bar charts, pie charts, and tables
Interactivity: Cross-filtering enabled across all visuals with slicers for Category, Brand, Country, and Year
