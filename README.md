# Data-Analysis-on-Walmart-Retail-Sales

## Table of Content 
- [Project overview](#project.overview)
- [Data source](#data.source)
- [Tools used](#tools.used)
- [Business questions](#business.questions)
- [Revenue and cost calculation](#revenueandcost.calculations)
- [Recommendation](#recommendations)

### Project Overview 
This project focuses on analyzing Walmart retail sales data to identify the top-performing branches and products, examine sales trends across various product categories, and gain insights into customer behavior. The objective is to explore ways to enhance and optimize sales strategies. 

### Data Source 
The primary dataset used for this analysis is the "Walmart_sales.csv", containing detailed information about each sales made by the company. The dataset used for this analysis was sourced from the Kaggle.

### Tools
- Excel - Data cleaning.
- MySQL - Data analysis.
- Power BI - Dashboards and report.

### Descriptive analysis performed 
1. Sales Analysis:

This analysis aims to examine sales trends across various products. The results will help evaluate the effectiveness of current sales strategies and identify any modifications needed to boost sales.

2. Product analysis:

Analyzed the data to identify the different product lines, determine which product lines are performing the best, and pinpoint those that require improvement.

3. Customer analysis:

This analysis aims to identify various customer categories, assess their purchasing patterns, and evaluate the profitability of each category.

## Data Wrangling: This is the first step where data profiling is carried out and inspection of data is done to make sure NULL values and missing values are detected and data replacement methods are used to replace, missing or NULL values.

1. Build a database
2. Create table and insert the data.
3. Select columns with null values in them. There are no null values in our database as in creating the tables, we set NOT NULL for each field, hence null values are filtered out in other to reduce the tendency of a baised finding.

## Feature Engineering: This process will help generate new columns based on the existing data.

- A new column, named *time_of_day*, has been added to provide insights into sales during different times of the day—Morning, Afternoon, and Evening. This will help address the question of which period sees the highest sales.

- A new column, *day_name*, has been added to extract the day of the week for each transaction (Mon, Tue, Wed, Thu, Fri). This will help determine which day of the week each branch is busiest.

- Another column, *month_name*, has been added to capture the month in which each transaction occurred (Jan, Feb, Mar). This will help identify the months with the highest sales and profit.

## Exploratory Data Analysis (EDA): EDA has been conducted to address the key questions and objectives of this project.

### Questions regarding Product
1. How many unique product lines does the data have?
2. What is the most common payment method?
3. What is the most selling product line?
4. What is the total revenue by month?
5. What month had the largest COGS?
6. What product line had the largest revenue?
7. What is the city with the largest revenue?
8. What product line had the largest VAT?
9. Fetch each product line and add a column to those product line showing "Good", "Bad". Good if its greater than average sales
10. Which branch sold more products than average product sold?
11. What is the most common product line by gender?
12. What is the average rating of each product line?

### Questions regarding sales
1. Number of sales made in each time of the day per weekday
2. Which of the customer types brings the most revenue?
3. Which city has the largest tax percent/ VAT (Value Added Tax)?
4. Which customer type pays the most in VAT?

### Questions regarding Customer
1. How many unique customer types are present in the data?  
2. How many distinct payment methods are used in the data?  
3. Which is the most common customer type?  
4. Which customer type makes the most purchases?  
5. What is the predominant gender among the customers?  
6. What is the gender distribution across each branch?  
7. At what time of day do customers give the most ratings?  
8. At what time of day do customers give the most ratings per branch?  
9. Which day of the week has the highest average ratings?  
10. Which day of the week has the highest average ratings per branch?

### Revenue And Profit Calculations
- $ COGS = unitsPrice * quantity $

- $ VAT = 5% * COGS $

- VAT is added to the COGS and this is what is billed to the customer.

- $ total(gross_sales) = VAT + COGS $

- $ grossProfit(grossIncome) = total(gross_sales) - COGS $

- Gross Margin is gross profit expressed in percentage of the total(gross profit/revenue)

- $ \text{Gross Margin} = \frac{\text{gross income}}{\text{total revenue}} $

Example with the first row in our Database:

Data given:

- $ \text{Unite Price} = $45.79
- $ \text{Quantity} = $7
- $ COGS = 45.79 * 7 = $320.53 

- $ \text{VAT} = 5% * COGS\= 5% 320.53 = $16.0265

- $ total = VAT + COGS\= 16.0265 + 320.53 = 336.5565

- $ \text{Gross Margin Percentage} = \frac{\text{gross income}}{\text{total revenue}}\=\frac{16.0265}{336.5565} = 0.047619\\approx 4.7619% $

### SQL Codes 

``` sql

-- Create database
CREATE DATABASE IF NOT EXISTS walmartSales;

-- Create table
CREATE TABLE IF NOT EXISTS sales(
	invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
);
```
### Results and findings 

The results of the analysis are summarised as follows; 
1. The food and breavage is the best selling product line category by revenue 
2. The Electronics and gadgets is the top selling product line category in terms of sales
3. The e-wallet method of payment should be targeted for marketing 
campaign and effort.

### Recommendation 

Based on the analysis, the following actions are recommended;
- Invest in marketing and promotion during the peak sales seasons to maximise revenue
- Focus on expanding and promoting product in the healthcare product line category
- Implement a customer segmentation strategy to target high-LTV customers effectively 
