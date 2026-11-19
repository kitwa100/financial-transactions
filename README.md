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
- This dataset contains tracking payment activity, spending patterns, and potential fraud across accounts. Each record represents a single monetary event captured with 11 core attributes. 
- A digital banking and cross-border payment provider, noticed a spike in disputed charges and failed settlements over a years window.

### Schema Overview

- Identifiers & Time. transaction_id (Primary Key) and transaction_date (ISO timestamp) track unique events and velocity.
- Account & Flow. account_type (Checking, Credit, Business, Savings) and transaction_type (Purchase, Transfer, Withdrawal, Refund) define the money movement.
- Valuation. amount (numeric) and currency (USD, EUR, KES, GBP) capture transaction scale and FX exposure.
- Context & Risk. merchant_category (e.g., Electronics, Travel, Crypto, Groceries), region (NA, EMEA, APAC, LATAM), status (Completed, Pending, Failed, Reversed), and is_flagged (Boolean) support compliance and risk scoring.


## Primary Problem Statement
The core objective is to predict whether a financial transaction is fraudulent or high-risk (is_flagged) based on its timing, monetary value, account details, and geographic context, while minimizing false positives for legitimate customers.  As a Data Analyst, you have been given the financial_transactions table to identify fraud patterns, isolate system bottlenecks, and recommend automated rule improvements.
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
   
| is_flagged |   |
| :--- | ---: | 
| 0.0 | 790  |
| 1.0 | 10 |

<img width="800" height="500" alt="overall_distribution" src="https://github.com/user-attachments/assets/1c897e1c-d7a1-47a6-8a54-f08f3f25b70d" />
<img width="948" height="500" alt="matric_ overall" src="https://github.com/user-attachments/assets/4bdc09e2-477b-4374-a2ed-74ddb5906a64" />


2. Which merchant_category or region experiences the highest volume of flagged transactions?

   - The Aggregation and Discovery Pipeline
           a. Merchant Category Flagged Volume
<img width="938" height="500" alt="Merchant Category" src="https://github.com/user-attachments/assets/c8cc3a8c-c14e-4f77-b3e8-03cca19a1dc3" />
  
           b. Regional Risk Mapping
<img width="938" height="500" alt="region_flagged" src="https://github.com/user-attachments/assets/a451790a-12c9-4a32-870b-e23e6b39b355" />
   - Advanced Multi-Dimensional Insights: Category × Region Matrix   

<img width="938" height="500" alt="multi_dimention" src="https://github.com/user-attachments/assets/8ef97900-f221-40b4-ae6b-eecd2cc1c64f" />
  
3. Are there specific account_type segments showing a disproportionate surge in failed or flagged transactions?
   
 | Total_transactions | Flagged_count | Flag_rate_%  | Surge_factor |
| :--- | :---: | :---: | ---: |
|152  |  2.0    |  1.315789     |  1.052632 |
|176  |  0.0    |  0.000000    |  0.000000 |
|172  | 3.0     |  1.744186     |  1.395349 |
|144  | 1.0     |  0.694444    |  0.555556 |
|156  | 4.0     |  2.564103   |  2.051282 |        
 <img width="938" height="500" alt="acc_flag" src="https://github.com/user-attachments/assets/6a1aefb4-d505-4c2e-9470-c9bf4576fe27" />
   
4. What is the total amount currently locked in a "failed" or "completed" status?

**Total Locked Amount (Failed + Completed): $94,530,101.90**

|  | status | total_amount | 
| :--- | :---: | ---:|
| 0  | Completed | 87592061.81 |
| 1  | Failed | 6938040.09 | 


<img width="700" height="500" alt="regional_share" src="https://github.com/user-attachments/assets/6bdd8cfd-76f9-4c6a-a34c-70283ef4ce37" />

### 2. Revenue & Growth Analytics
1. What is our transaction_date growth rate in total transaction amount split by currency?

2. Which merchant_category driving the highest average order value (AOV)?
   
4. What are the top 3 performing region markets by transaction volume and total value?
6. How does the volume of transaction_type (e.g., deposits vs. withdrawals) fluctuate across different seasons or days of the week?
### 3. Customer Segmentation & Engagement
1. How do spending habits (amount and merchant_category) differ between various account_type tiers (e.g., Retail vs. Corporate)?
2. What is the velocity of transaction_date for our most active account_type?
3. Which region shows the highest preference for the transaction_type?

### 4. Operational Efficiency
1. What percentage of total transactions result in a "failed" status, and what is the associated financial impact?
2. What is the ratio of inbound to outbound transactions (transaction_type) across transaction_date?

## Insights
### - Fraud & Risk Management
1. In financial transaction monitoring, rule-based fraud flags typically yield an exceptionally high false positive rate (FPR) of 90% to 98%. This means that out of every 100 alerts generated by your automated "is flagged" system, only 2 to 10 represent actual fraudulent activity, while the rest are legitimate customer transactions. 
<img width="1000" height="1200" alt="revenue and growth" src="https://github.com/user-attachments/assets/f48a1c6f-7928-4170-aa6d-b2c49423105a" />
Key Operational Insights
- Static Threshold Limitations: Blunt rules—such as flagging all transfers over a specific dollar amount—fail to account for normal individual baseline behaviors. A high-net-worth individual making a standard high-value transfer triggers the same flag as a genuine fraudster. 
- The Alert Volume Paradox: In an effort to minimize false negatives (missing actual fraud), systems are calibrated too aggressively.
- This floods manual review teams with non-fraud alerts, creating massive operational backlogs and analyst fatigue. 
- Severe Bottom-Line Friction: False declines are highly damaging to customer retention. Industry data indicates up to 40% of consumers will completely stop doing business with a merchant or financial provider after experiencing a single false decline. 

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



