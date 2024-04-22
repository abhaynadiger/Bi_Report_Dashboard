Credit_Card_Financial_Dashboard

Project Objective
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, 
enabling stakeholders to monitor and analyze credit card operations effectively.

Credit card financial dashboard using Power BI:
• Developed an interactive dashboard using transaction and customer data from a SQL database, to provide real-time insights.
• Streamlined data processing & analysis to monitor key performance metrics and trends.
• Shared actionable insights with stakeholders based on dashboard findings to support decision-making processes.

DashBoard Reports:
![Alt text](https://github.com/abhaynadiger/Bi_Report_Dashboard/Credit Card Financial Dashboard-Customer.png)?raw=true "Credit Card Financial Dashboard-Customer")

Project Insights:
• Revenue increased by 28.8%,
• Total Transaction Amt & Count increased by xx% & xx%
• Customer count increased by xx%
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall transactions
• TX, NY & CA is contributing to 68%

Import data to SQL database
1. Prepare csv file
2. Create tables in SQL
3. import csv file into SQL

DAX Queries
1) AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)

2) IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)

3) week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

4) Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))
