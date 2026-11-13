# financial-transactions

### Table of content
- [Project overview](#Project-overview)
- [Data sources](#Data-sources)
- [Tools](#Tools)
- [Data cleaning](#Data-cleaning)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Insights](#Insights) 
- [Recommendations](#Recommendations)

## Project overview
This dataset contains tracking payment activity, spending patterns, and potential fraud across accounts. Each record represents a single monetary event captured with 11 core attributes. 

## Data sources
- Project Jupyter notebook
  
## Tools
- excel
- python
- pandas
- matplotlib
- plotly express
- Numpy
- seaborn

## Data cleaning
1. Changing the datatype 
2. Removing duplicate

## Exploratory Data Analysis
### 1. Fraud & Risk Management
1. What is the overall false positive rate of our fraud flags (is_flagged)?
2. Which merchant_category or region experiences the highest volume of flagged transactions?
   - The Aggregation and Discovery Pipeline 
   - Advanced Multi-Dimensional Insights: Category × Region Matrix   
  
4. Are there specific account_type segments showing a disproportionate surge in failed or flagged transactions?
5. What is the total amount currently locked in a "failed" or "completed" status?

### 2. Revenue & Growth Analytics
1. What is our transaction_date growth rate in total transaction amount split by currency?
2. Which merchant_category driving the highest average order value (AOV)?
3. What are the top 3 performing region markets by transaction volume and total value?
4. How does the volume of transaction_type (e.g., deposits vs. withdrawals) fluctuate across different seasons or days of the week?
### 3. Customer Segmentation & Engagement
1. How do spending habits (amount and merchant_category) differ between various account_type tiers (e.g., Retail vs. Corporate)?
2. What is the velocity of transaction_date for our most active account_type?
3. Which region shows the highest preference for the transaction_type?

### D. Operational Efficiency
1. What percentage of total transactions result in a "failed" status, and what is the associated financial impact?
2. What is the ratio of inbound to outbound transactions (transaction_type) across transaction_date?

## Insights
- Fraud & Risk Management

1. Overall churn rate: 26.54% (1,869 churned customers)
- Revenue & Growth Analytics
- Customer Segmentation & Engagement
- Operational Efficiency

| **Total Customers:** 7043 |
| --- |
| **Churned Customers:** 1869 |
| **Baseline Churn Rate:** 26.54% |





Churn Rate by Demographics 

| churn | senior_citizen | dependents |Churn Rate (%) |
| :--- | :---: | :---: | ---: |
|0  |  0    |  No     |  29.60 |
|1  |  0    |  Yes    |  16.05 |
|2  | 1     |  No     |  32.64 |
|3  | 1     |  Yes    |  19.78 |




### Services & Product Performance




### Financial Impact & Contract Optimization



## Recommendations

