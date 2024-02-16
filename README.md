# Telecom Customer Churn-Analysis - Power BI

## Background
Customers in the telecom industry are hard-earned, and like the Retention Manager from our telecom Client, no brand wants to lose them. A few weeks after presenting the [Telecom Customer Churn Analysis - Power-BI](https://github.com/shantanu1109/Telecom-Customer-Churn-Analysis-Power-BI) dashboard to the management, the Retention Manager from the telecom reached out directly to Shantanu. He was impressed by the work and asked for a dashboard about customer retention.

In addition, to better understand the data, the telecom Retention Manager has scheduled a meeting with the engagement partner at PwC to cover these points:

Customers in the telecom industry are hard-earned: we don’t want to lose them
The retention department is here to get customers back in case of termination 
Currently, we get in touch after they have terminated the contract, but this is reactionary: it would be better to know in advance who is at risk 
We  have done customer analysis with Excel: it has always ended in a dead-end
We would like to know more about our customers: visualised clearly so that it’s self-explanatory for our management
The Retentions Manager has provided some information in the resources.


This project, part of PwC's virtual case experience program, aimed to develop a dashboard highlighting crucial customer-retention metrics and conduct an analysis to identify key factors influencing customer churn.

### Overview:
The main page illustrates the primary factors impacting customer churn alongside key performance indicators (KPIs).

### Customer Demographics:
On this page, churn rates are depicted based on demographic data such as gender, age range, and whether customers have partners or dependents.

### Account Details: 
This section visualizes churn rates based on various customer account details including tenure, contract type, payment method, paperless billing, monthly charges, total charges, and the number of administrative and technical support tickets opened.

### Subscription: 
Here, churn rates are presented based on the services each customer has subscribed to, including phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies.

### Customer Info: 
This page provides a comprehensive profile of each customer, allowing for the lookup of specific customer information.

### Key Insights: 
The final section summarizes significant findings and conclusions drawn from the analysis.


Total Customers = COUNT(ChurnDataset[CustomerID])
Churned Customers = CALCULATE(COUNTA('ChurnDataset'[CustomerID]), 'ChurnDataset'[Churn] IN { "Yes" })
Retained Customers = CALCULATE(COUNTA('ChurnDataset'[CustomerID]), 'ChurnDataset'[Churn] IN { "No" })
Churn Rate % = ChurnDataset[Churned Customers] / COUNT(ChurnDataset[CustomerID])
Monthly Revenue Loss = CALCULATE(SUM(ChurnDataset[MonthlyCharges]), ChurnDataset[Churn] = "Yes")
Revenue Loss % = DIVIDE([Monthly Revenue Loss], SUM('ChurnDataset'[MonthlyCharges]), 0)
ChurnStatus = IF('ChurnDataset'[Churn] = "Yes", "Churned", "Retained")
CitizenshipStatus = IF('ChurnDataset'[SeniorCitizen] = 0, "Young Citizen", "Senior Citizen")
PaymentMode = IF(OR('ChurnDataset'[PaymentMethod] = "Electronic Check", 'ChurnDataset'[PaymentMethod] = "Mailed Check"), "Manual", "Automatic")
Percent of Churned Customer = (ChurnDataset[Churned Customers] / [Total Customers])
Percent of Retained Customers = ([Retained Customers] / [Total Customers])
