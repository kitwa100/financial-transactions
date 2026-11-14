# FINANCIAL TRANSACTIONS

### Table of content
- [Project overview](#Project-overview)
- [Primary Problem Statement](#Primary-Problem-Statement)
- [Data sources](#Data-sources)
- [Tools](#Tools)
- [Data cleaning](#Data-cleaning)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Insights](#Insights) 
- [Recommendations](#Recommendations)

## Project overview
This dataset contains tracking payment activity, spending patterns, and potential fraud across accounts. Each record represents a single monetary event captured with 11 core attributes. 

## Primary Problem Statement
The core objective is to predict whether a financial transaction is fraudulent or high-risk (is_flagged) based on its timing, monetary value, account details, and geographic context, while minimizing false positives for legitimate customers.
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
### - Fraud & Risk Management
1. Combining is_flagged, amount, region, and status helps you identify suspicious activity and tune your fraud rules.
2. Flagged Transaction Rate: Divide flagged transactions by total transactions to establish a baseline risk rate. Group this metric by region and merchant_category to spot high-risk clusters.
3. High-Value Anomaly Detection: Compare amount distributions for is_flagged = True against normal transactions within the same account_type. Look for sudden spikes in transaction size or rapid repeat transactions on the same transaction_date.
4. False Positive Evaluation: Cross-reference is_flagged with status (e.g., completed vs. blocked). A high volume of flagged transactions that ultimately clear safely indicates overly strict fraud filters.
<img width="1000" height="1200" alt="revenue and growth" src="https://github.com/user-attachments/assets/f48a1c6f-7928-4170-aa6d-b2c49423105a" />

### - Revenue & Growth Analytics
1. Using transaction_date, transaction_type, amount, and currency reveals the overall financial health and seasonality of the accounts.
2. Net Cash Flow: Subtract outgoing transaction_type totals (debits, withdrawals, fees) from incoming totals (credits, deposits, refunds) over daily, weekly, or monthly windows.
3. Currency Exposure: Group amount by currency to see which currencies drive the most volume. Normalize all values to a single base currency using historical exchange rates before calculating global totals.
4. Seasonality & Peak Periods: Aggregate transaction counts and total volume by day of the week or month using transaction_date. This helps forecast liquidity needs and peak processing times.
<img width="1200" height="1000" alt="segmentation" src="https://github.com/user-attachments/assets/c26d7428-2e2f-4c1d-afb3-22a5d128ae8e" />

### - Customer Segmentation & Engagement
1. Analyzing account_type alongside spending habits shows how different user tiers use their accounts.
2. Spend per Account Tier: Calculate the average transaction value (amount) and transaction frequency per account_type (e.g., personal, business, premium).
3. Category Preferences: Map merchant_category against account_type to see where different segments spend most, such as travel and software for business accounts versus groceries and retail for personal accounts.


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


## Recommended Summary Metrics Table



