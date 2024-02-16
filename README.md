<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

<div align="center">
    <h2 style="font-size: 44 px;"> Telecom Customer Churn-Analysis - Power BI </h2><br>
</div>

<div align= "center">
    <img src="https://blog.salespanel.io/wp-content/uploads/2022/06/image1-02.jpg">
</div>

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## Background
Customers in the telecom industry are hard-earned, and like the Retention Manager from our telecom Client, no brand wants to lose them. A few weeks after presenting the [Telecom Customer Churn Analysis - Power-BI](https://github.com/shantanu1109/Telecom-Customer-Churn-Analysis-Power-BI) dashboard to the management, the Retention Manager from the telecom reached out directly to Shantanu. He was impressed by the work and asked for a dashboard about customer retention.

Additionally, the telecom Retention Manager scheduled a meeting with the engagement partner at PwC to better understand the data. Some points covered in the meeting include:

- Proactive Customer Retention: In the telecom industry, retaining customers is paramount. The retention department's primary objective is to re-engage customers in the event of contract termination. Presently, their approach is reactionary, reaching out post-termination. However, a proactive strategy to identify at-risk customers beforehand would be more effective.

- Past Analysis Limitations: Previous attempts at customer analysis using Excel have proven fruitless, resulting in dead-ends. This underscores the necessity for a more sophisticated and efficient analytical approach.

- Enhanced Customer Insight: There's a pressing need for comprehensive customer analysis within the telecom sector. Visual representations of this data, designed to be self-explanatory, are essential for effective communication with the management team. The retention manager has provided some resources to facilitate this process, highlighting its importance.

The retention manager also provided more context to the required dashboard through the email shown below
![](Image-1-Retention-Manager-Input.JPG)

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
