<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

<div align="center">
    <h2 style="font-size: 44 px;"> Telecom Customer Churn-Analysis - Power BI </h2><br>
</div>

<p align="center">
  <img src="https://img.shields.io/github/repo-size/shantanu1109/Telecom-Customer-Churn-Analysis-Power-BI" alt="GitHub repo size">
  <img src="https://custom-icon-badges.demolab.com/github/last-commit/shantanu1109/Telecom-Customer-Churn-Analysis-Power-BI?logo=history&logoColor=white" alt="GitHub last commit">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?logo=github" alt="Status">
</p>

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
![](Project-Images/Image-1-Retention-Manager-Input.JPG)

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## Project Details
**What is Churn?** \
**Churn** refers to the rate at which customers stop doing business with a company or service, typically expressed as a percentage of the customer base.

**What is a Churn Rate?** \
**Churn Rate**, sometimes known as attrition rate, is the rate at which customers stop doing business with a company over a given period. Churn may also apply to the number of subscribers who cancel or don’t renew a subscription. The higher your churn rate, the more customers stop buying from your business. The lower your churn rate, the more customers you retain. Typically, the lower your churn rate, the better.

> **Churn Rate** = (Churned Customers / Total Number of Customers) x 100%

**What is Customer Churn?** \
Customer Churn refers to the natural business cycle of losing and acquiring customers. Every company — no matter the quality of its products or customer service experiences churn. In the context of businesses, customer churn can occur due to factors such as dissatisfaction with the product or service, competitive offerings, or changes in circumstances or preferences of the customer. Generally speaking, the less churn a company has, the more customers they keep.

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## About the Data
The dataset is a Microsoft Excel file that contains one table, consisting of **7,043 rows and 23 columns** of **PhoneNow Telecoms** customer information, which includes, customer Demographics, Account Information, and Service Subscriptions. The data was gotten from [Forage]( https://cdn.theforage.com/vinternships/companyassets/4sLyCPgmsy8DA6Dh3/02%20Churn-Dataset.xlsx).

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## Skills

```
- Data Cleaning
- Data Inspection
- Data Transformation
- Data Standardization
- Data Visualization
```

> **Data Inspection:** Visually inspect the data to identify errors, inconsistencies, or missing values.

> **Data Transformation:** Converting data from one format or structure to another, to make it more suitable for a specific task or analysis.

> **Data Standardization:** Converting data into a standard format, such as converting all text to lowercase or standardizing date formats.

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## Data Preparation

The data transformation was finished using Power Query, and now the dataset is loaded into Microsoft Power BI Desktop for modeling purposes.

1. The Customer Churn dataset is given table named:

> - ChurnDataset which has 7043 rows and 23 columns of observation.

2. Data Cleaning for the dataset was done in the **Power Query Editor** as follows:

- Changed the Data type of customerID, gender, SeniorCitizen as given below:
> = Table.TransformColumnTypes(#"Promoted Headers",{{"customerID", type text}, {"gender", type text}, {"SeniorCitizen", Int64.Type}, 

- Replaced Value names of Mailed check, Electronic check, Bank transfer (automatic), Credit card (automatic) in the columns as given below:
```
1. = Table.ReplaceValue(#"Changed Type","Mailed check","Mailed Check",Replacer.ReplaceText,{"PaymentMethod"})
2. = Table.ReplaceValue(#"Replaced Value","Electronic check","Electronic Check",Replacer.ReplaceText,{"PaymentMethod"})
3. = Table.ReplaceValue(#"Replaced Value1","Bank transfer (automatic)","Bank Transfer",Replacer.ReplaceText,{"PaymentMethod"})
4. = Table.ReplaceValue(#"Replaced Value2","Credit card (automatic)","Credit Card",Replacer.ReplaceText,{"PaymentMethod"})
```

- Replaced Column Names of customerID, gender, tenure as given below:
> = Table.RenameColumns(#"Replaced Value3",{{"customerID", "CustomerID"}, {"gender", "Gender"}, {"tenure", "Tenure"}})

3. In the new table, two additional conditional columns were added using M-formula:
```
1. = CitizenshipStatus = IF('ChurnDataset'[SeniorCitizen] = 0, "Young Citizen", "Senior Citizen")
2. = ChurnStatus = IF('ChurnDataset'[Churn] = "Yes", "Churned", "Retained")
```
<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>

## Data Modeling

Then dataset was cleaned and transformed, it was ready for the data modeled.

The customer churn tables as shown below
![](Project-Images/Image-2-Data-Modeling.png)

<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"></a>


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
