# Credit_Card_Financial_Dashboard
### Credit Card Transaction and Customer Dashboard using Power BI

### **Content
#### 1. Project objective
#### 2. Data from SQL
#### 3. Data processing & DAX
#### 4. Dashboard & insights

#### 1. Project Objective
##### To develop an interactive and real-time weekly dashboard for credit card operations that highlights key performance indicators (KPIs), customer behavior, and operational trends. This dashboard will support stakeholders in making informed decisions, tracking performance efficiently, and identifying areas for improvement to enhance overall business outcomes.

#### 2.Import data to SQL database

##### 1. Prepare csv file
##### 2. Create tables in SQL
##### 3. import csv file into SQL

#### 3. DAX Queries

1.
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)

2.
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)

3.
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))


#### Project Insights- Week 53 (31st Dec)
WoW change:
• Revenue increased by 28.8%,
• Total Transaction Amt & Count increased by xx% & xx%
• Customer count increased by xx%
Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall
transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%
