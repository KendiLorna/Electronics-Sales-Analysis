## Electronics-Sales-Analysis(2016-2021)

## Tool: Microsoft Power BI

### Project Overview
This project presents a comprehensive analysis of electronics sales data spanning from 2016 to 2021.
The interactive Power BI dashboard provides insights into revenue, profitability, customer behavior, product and store performance, and geographic distribution across multiple dimensions.

### Business Context
The analysis examines an electronics retail business operating across multiple countries with both physical stores and online presence.
The dashboard enables stakeholders to understand key business metrics and trends over a six-year period, including the impact of market changes in 2020-2021.

### Business Questions
#### 1. Overall Performance (KPI Tracking)

What is our total revenue, profit, quantity sold, and customer count?

Are these KPIs growing or declining compared to targets?

#### 2. Trends Over Time (Monthly Analysis)

How have revenue, profit, quantity, and customer count changed month by
month since 2020?

Are there seasonal patterns or months where performance consistently drops?

#### 3. Year-over-Year (YoY) Comparison

How does performance in the current year compare to previous years?

What is the YoY growth/decline % for revenue, profit, and customers?

Are we recovering or still trending downward?

#### 4. Product Performance
Which products, categories, and subcategories are driving revenue and profit
growth?

Which ones are underperforming and contributing to the decline?

What are the top 10 best-sellers vs. the bottom 10 laggards?

Are our profit margins shrinking due to rising costs or discounting?

#### 5. Customer Insights

Who are our customers? (gender, age, geography)

Are we losing existing customers or failing to attract new ones?

Which customer segments contribute the most to revenue and profit?

Are younger or older demographics shifting their buying behavior?

#### 6. Store & Regional Performance

Which stores, states, and countries are performing well vs. declining?

Are certain regions driving the overall revenue decline?

How does store performance vary based on open date (new vs. old stores)?

### Data Structure
The dataset includes the following key information:

- Time Period: 2016-2021

- Geographic Coverage: United States, United Kingdom, Germany, Canada, Australia, France, Italy, Netherlands, and Online sales

- Product Categories: Computers, Home Appliances, Cameras and Camcorders, Cell Phones, TV and Video, Audio, Music/Movies/Audio Books, Games and Toys

- Brands: 11 major brands including Adventure Works, Wide World Importers, Contoso, Fabrikam, and others

### Data Model

<img width="1650" height="765" alt="Screenshot 2025-09-29 170438" src="https://github.com/user-attachments/assets/986be9d7-5b0c-4e1a-b232-652f384e9582" />

### Data Preparation
Calculated Measures Created
I developed several DAX measures to enable comprehensive analysis:

Total Revenue 
```
Revenue = SUMX(Sales,Sales[Quantity]*RELATED(Products[Unit Price USD]))
```
Total Cost
```
Cost = SUMX(Sales,Sales[Quantity]*RELATED(Products[Unit Cost USD]))
```
Total Profit
```
Total Profit = [Revenue]-[Cost]
```
YoY Revenue change
```
YoY Revenue % = 
VAR Curr_Sales = [Revenue]
VAR PY_Sales = CALCULATE([Revenue],SAMEPERIODLASTYEAR('Date'[Date]))

VAR YoY_Change = DIVIDE(Curr_Sales-PY_Sales,PY_Sales)

VAR _Format = SWITCH(
            TRUE(),
            YoY_Change > 0,UNICHAR(11165) & " " & FORMAT(YoY_Change,"0.0%"),
            YoY_Change < 0,UNICHAR(11167) & " " & FORMAT(YoY_Change,"0.0%"),
            FORMAT(YoY_Change,"0.0%")
            )
RETURN 
        _Format
```
KPIs
```
KPIs = {
    ("Total Revenue", NAMEOF('Measures Table'[Revenue]), 0),
    ("Total Profit", NAMEOF('Measures Table'[Total Profit]), 1),
    ("Quantity Sold", NAMEOF('Measures Table'[Quantity Sold]), 2),
    ("Total Cost", NAMEOF('Measures Table'[Cost]), 3)
}
```
Calculated Columns:
- Age
```
`Age = DATEDIFF('Customers (2)'[Birthday],MAX('Date'[Date]),YEAR)``
```
- Age Groups
```
Age Buckets = 
VAR age = 'Customers (2)'[Age]
RETURN SWITCH(
    TRUE(),
    age >=19 && age <= 29,"19-29",
    age > 29 && age <= 39, "30-39",
    age > 39 && age <= 49, "40-49",
    age > 49 && age <= 59, "50-59",
    age > 59 && age <= 69, "60-69",
    age > 69 && age <= 79, "70-79",
    "80+")
```

Created a date table for time series analysis.

### Key Insights

## Overview
<img width="1440" height="805" alt="Overview" src="https://github.com/user-attachments/assets/413aa0d4-c5e0-4d0f-b02c-96e0e2925aa3" />

#### Overall Performance

Total Revenue: $55.76M (up 1.9% YoY)

Total Profit: $32.66M (up 1.9% YoY)

Quantity Sold: 197.76K units (up 2.0% YoY)

Customer Base: 11.89K customers (up 0.6% YoY)

Total Orders: 62.88K (up 2.0% YoY)

#### Seasonal Patterns

Significant revenue decline in March-April, with recovery beginning in May and stabilization through year-end.

January-February: Strong start with revenue peaking around $2.5-3M.

March Crisis: Dramatic revenue collapse to below $500K (likely COVID-19 impact)

April: Lowest point of the year (~$400K)

May-December: Gradual recovery and stabilization at $800K-$1M monthly.

No traditional holiday spike: December shows no significant uptick.

## Customers
<img width="1436" height="799" alt="Customers" src="https://github.com/user-attachments/assets/ea701bf7-bb91-44d7-8f5b-cb0adee3f30b" />

#### Customer Demographics

Nearly balanced gender distribution (49% female, 51% male)

Peak customer concentration in 19-29 age group (1.82K customers)

Strong representation across middle-age groups (30-59)

There is a steep loss of customers from 2019-2021.

Younger demographics (19-39) are not driving growth - all age groups show similar purchasing patterns

Computer and cell phone purchases are consistent across all ages.

There is no evidence of age-based behavioral shifts, there is a  loss of customers across all segments, not demographic preference changes.

## Products
<img width="1436" height="803" alt="Products" src="https://github.com/user-attachments/assets/35a9196f-3c3d-4066-ab38-c52173e376ff" />


#### Product Category Insights

Computers lead in revenue and profit generation.

Strong performance in Home Appliances category.

Games and Toys show consistent demand across age groups.

Profit Margin Concern: Costs are growing in line with revenue (both +1.9%), suggesting margins are stable but not improving.

## Stores
<img width="1435" height="804" alt="Stores" src="https://github.com/user-attachments/assets/5b564902-3c7e-4fec-a59b-594158fb5470" />

#### Geographic Performance

United States dominates with 5.71K customers which translates to the high revenue of $4.6M.

Strong European presence led by United Kingdom (1.57K customers)

#### Store Performance

Peak Performance: Stores operating 14 years ($18.9M revenue)

Strong Performance: 10 years ($7.7M), 12 years ($1.9M)

Stores reach peak performance around 10-14 years, then decline as they age.

Online purchases bring in the most revenue at $2.4M.

### Recommendations

Observe trends and implement necessary operational changes post-covid.

Rationalize product portfolio (eliminate lighting/low performers)

Focus marketing on 19-59 age demographics across all regions.

Optimize store portfolio - close underperforming locations due to age or size which seem to increase operation costs.

Strengthen the online channel-store 0 since it can serve multiple locations and performs well across years.

Marketing campaigns to attract and keep new customers.

View the interactive dashboard [here]([https://app.powerbi.com/view?r=eyJrIjoiNWJhNTZjNjQtMWMzOC00YWEyLTgyMzMtZjM1NDJlOGJhYzhkIiwidCI6IjE5Mzc0NTc0LTFlMGEtNDJlZi1iMTBkLWRhNDRkODI0OGE4YiJ9](https://app.powerbi.com/view?r=eyJrIjoiNWJhNTZjNjQtMWMzOC00YWEyLTgyMzMtZjM1NDJlOGJhYzhkIiwidCI6IjE5Mzc0NTc0LTFlMGEtNDJlZi1iMTBkLWRhNDRkODI0OGE4YiJ9))
