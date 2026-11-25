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
- This dataset contains tracking payment activity, spending patterns, and potential fraud across the dataset. Dataset is structured to support fraud detection, financial operations monitoring, and spending analytics.

### Schema Overview

- Identifiers & Time. transaction_id (Primary Key) and transaction_date (ISO timestamp) track unique events and velocity.
- Account & Flow. account_type (Checking, Credit, Business, Savings) and transaction_type (Purchase, Transfer, Withdrawal, Refund) define the money movement.
- Valuation. amount (numeric) and currency (USD, EUR, KES, GBP) capture transaction scale and FX exposure.
- Context & Risk. merchant_category (e.g., Electronics, Travel, Crypto, Groceries), region (NA, EMEA, APAC, LATAM), status (Completed, Pending, Failed, Reversed), and is_flagged (Boolean) support compliance and risk scoring.


## Problem Statement

- Background: The core objective is to predict whether a financial transaction is high-risk (is_flagged) based on its timing, monetary value, account details, and geographic context, while minimizing false positives for legitimate customers.  

- Problem: Legitimate transactions are occasionally delayed or declined, while fraudulent transactions slip through unnoticed, leading to direct financial loss and poor customer experience.
  
- Objective: Analyze historical transaction patterns—specifically examining amount, merchant_category, region, account_type, and status—to identify the primary drivers behind is_flagged events and build a predictive model or rule-based system to detect high-risk transactions in real time.

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

<img width="930" height="500" alt="Total Amount" src="https://github.com/user-attachments/assets/7baa8474-ac4f-4d70-9aaa-b8708f34e50e" />


### 2. Revenue & Growth Analytics
1. What is our transaction_date growth rate in total transaction amount split by currency?
<img width="700" height="500" alt="trans_growth" src="https://github.com/user-attachments/assets/9d180d55-0258-4cfd-a41c-fd39c7738ca1" />

2. Which merchant_category driving the highest average order value (AOV)?

**Highest AOV Category: Unknown ($286,211.84)**

|  | merchant_category    |    aov | median_value | transaction_count    |   std_dev |
|:---|:---:|:---:|:---:|:--:|--:|
| 9   |         Unknown | 286211.84   |   62328.65        |         41 | 1.390083e+06 |
| 5   |         Grocery | 169460.90    |  68073.51         |        83 | 6.386805e+05 |
| 3    |  Entertainment | 157728.88   |   96269.16        |         77 | 6.181063e+05 |
| 10    |     Utilities | 156858.25   |   79261.71         |        93 | 7.906672e+05 |
| 8      |       Travel | 132595.70   |   79138.44         |        72 | 4.913667e+05 |
| 0       |      Dining | 129301.00   |   74430.69          |       68 | 4.686837e+05 |
| 6    |     Healthcare  | 90502.34   |   74311.08          |       69 | 1.214689e+05 |
| 1     |     Education  | 82986.41   |   57754.25          |       75 | 1.386169e+05 |
| 2      |  Electronics  | 79989.18   |   79388.22          |       72 | 4.112790e+04 |
| 4       |        Fuel  | 69988.85   |   61486.24           |      81 | 4.365862e+04 |
| 7   | Online Shopping  | 69283.35   |   74461.02            |     69 | 4.335242e+04 |

<img width="930" height="500" alt="avg order" src="https://github.com/user-attachments/assets/e4ac98bc-006c-46b6-8bed-d25fc4a06ba6" />

   
3. What are the top 3 performing region markets by transaction volume and total value?

**Top 3 Regions by Transaction Volume:**

|      |    region | transaction_volume |
| :--- | :--: | --: |
| 2 | International   |              133 |
| 7  |         West    |             128 |
| 1   |        East     |            120  |

**Top 3 Regions by Total Value:**

|    |   region | total_value |
|:--- |:--: |--:|
| 5   |    South |  21751975.80 |
| 0    | Central | 16469034.91 |
| 4 | North-East | 14926623.59 |

<img width="920" height="360" alt="Transaction Volume" src="https://github.com/user-attachments/assets/e0f55310-4a75-4405-b105-6f6b4c0eef46" />

<img width="920" height="500" alt="Total Value" src="https://github.com/user-attachments/assets/200768eb-2e77-48a4-920d-67050215e04a" />

4. How does the volume of transaction_type (e.g., deposits vs. withdrawals) fluctuate across different seasons or days of the week?
<img width="930" height="500" alt="Over Time by Type" src="https://github.com/user-attachments/assets/5003d5c6-d639-4134-8299-2e5b6d3a28f8" />

   
### 3. Customer Segmentation & Engagement

1. How do spending habits (amount and merchant_category) differ between various account_type tiers (e.g., Retail vs. Corporate)?
    - **Data Preparation & Summary Statistics (pandas & numpy)**
First, clean the data to isolate spending (debits/outflows) if your dataset also includes deposits, and calculate key summary metrics—including the median and IQR (Interquartile Range), which are more reliable than the mean when large outliers skew transaction amounts

**Overall Spending Metrics by Account Type**

| account_type | transaction_count | total_spend | mean_spend | median_spend |
|:---|:---:|:---:|:---:|--:|
| 3    |   Salary       |         144 | 26520040.24 |  184166.95  |    62790.70  | 
| 1    |  Current       |        176 | 21503882.74 |  122181.15   |   79059.23   |
| 4   |   Savings       |       156 | 17962963.13 |  115147.20   |   72676.21   |
| 2   |       NRE       |      172 | 16826987.26  |  97831.32   |   68252.52   |
| 0   |   Credit Card   |       152 | 16735877.14 |  110104.45   |  75063.10   |

|  |  std_dev | p90_spend |
|:--- | :---:|---:|
| 3 | 973570.91 | 133230.28 | 
|1 | 419242.37 | 136460.59  |
| 4 | 442506.02 | 138329.72 | 
| 2 | 326769.88 | 137015.47  |
| 0 | 351141.93 | 138239.96  |

   - **Category Share & Relative Preference**
     
Raw totals can be misleading if one account type simply has more users. Normalizing spending as a percentage of each account's total spend reveals true behavioral preferences (e.g., whether Current accounts skew toward utilities/B2B while Credit Card skews toward dining and travel)

**Percentage of Total Spend by Category**

| account_type   |    Credit Card | Current  |  NRE | Salary | Savings |
| :--- |:---:|:---:|:---:|:---:|---:|
| merchant_category |                |     |    |  |   |                      
| Dining         |           5.27   | 22.56  | 5.37  |  4.58 |    5.24 |
| Education       |         15.04    | 4.17 |  7.84   | 1.90  |   5.49 |
| Electronics       |        6.77   |  6.70  | 7.30  |  4.15   |  4.77 |
|Entertainment      |      12.49    | 6.32  | 7.09  |  3.52  |  36.56 |
|Fuel               |       6.95 |    2.95  | 8.00  |  4.75  |   7.04 |
|Grocery           |        4.35  |  26.22 | 35.84   | 1.91 |    6.48 |
|Healthcare             |   5.66  |   8.12 |  5.96  |  3.27  |   9.36 |
|Online Shopping      |     3.37   |  6.20  | 5.53  |  2.71   |  6.87 |
|Travel               |    30.92   |  6.30  | 4.54  |  3.33    | 7.63 |
|Unknown              |     1.75   |  3.55  | 4.83  | 35.01  |   3.23 |
|Utilities               |  7.42  |   6.92 |  7.69 |  34.88  |   7.32 |




A. Transaction Size Distribution (Box Plot)¶
A box plot on a logarithmic scale handles extreme outliers well while clearly showing differences in median transaction sizes across accounts.

<img width="930" height="500" alt="Account Type" src="https://github.com/user-attachments/assets/586ee2bf-ac22-4cf6-a7bc-e67253bea82e" />

B. Category Mix Comparison (100% Stacked Bar Chart)¶
This chart makes it immediately obvious which merchant categories dominate each account type's budget.

<img width="930" height="500" alt="Share of Total" src="https://github.com/user-attachments/assets/b522a1b6-b0c6-418c-a69d-04dcc1f90e17" />

C. Frequency vs. Ticket Size Matrix (Heatmap)¶
A heatmap highlights exact pockets of high-value spending across categories and accounts.

<img width="930" height="500" alt="Median Transaction" src="https://github.com/user-attachments/assets/c9f82cbe-0591-4844-a2ed-6d5a29e15702" />
2. What is the velocity of transaction_date for our most active account_type?
     - Most Active Account Type: **Current**
     - Average Velocity: **0.24 transactions/day**

<img width="930" height="500" alt="Transaction Velocity" src="https://github.com/user-attachments/assets/6f36ca5e-3eef-4370-967f-f5918590ee8c" />
   
4. Which region shows the highest preference for the transaction_type?
   **Highest Preference Region per Transaction Type**
   
| transaction_type  |   region  | preference_pct |
|:--|:--:|--:|
| Deposit    |  North | 22.12 |
| Fee  |  Unknown |   100.00 |
| Purchase   |   South |   21.50 |
| Refund | North-East  |   19.79 |
| Transfer   |    West     |      20.31 |
| Withdrawal  |  Central |    18.02 |
      
<img width="700" height="500" alt="regional_share" src="https://github.com/user-attachments/assets/6bdd8cfd-76f9-4c6a-a34c-70283ef4ce37" />

### 4. Operational Efficiency
1. What percentage of total transactions result in a "failed" status, and what is the associated financial impact?
        - Failed Transactions: 40 out of 800 (5.00%)
        - Financial Impact: $6,938,040.09 (6.97% of total volume)

<img width="938" height="500" alt="Financial Impact" src="https://github.com/user-attachments/assets/76aed3aa-00c2-427d-9e18-3bc52a40f81f" />

<img width="938" height="500" alt="bar financial impact" src="https://github.com/user-attachments/assets/12e06cb1-a3a5-4881-a892-0a10f330d8c3" />

2. What is the ratio of inbound to outbound transactions (transaction_type) across transaction_date?

<img width="700" height="500" alt="in out bound" src="https://github.com/user-attachments/assets/1f6cbfa6-8634-4792-84d8-a31740207626" />


## Insights

1. Fraud & Risk Management

2. Revenue & Growth Analytics

3. Customer Segmentation & Engagement

4. Operational Efficiency


## Recommendations

1. Fraud & Risk Management

2. Revenue & Growth Analytics

3. Customer Segmentation & Engagement

4. Operational Efficiency
