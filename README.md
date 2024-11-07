# LITA-CAPSTONE-PROJECT-CUSTOMER-DATA

## Table of Content 
- Overview
- Data Sources
- Tools Used
- Data Cleaning and Preparation
- Exploratory Data Analysis
- Data Analysis
- Visualization and Inference
- Recommendations
- Limitations
----------------------------------------------------------------------------
### Project Overview

This project aims to analyze customer data for a subscription based service to identify distinct customer subscription trend, understand their behavior and track trends in subscriptions and cancellations. This analysis will identify and characterize customer segments based on demographic and behavioral factor, analyze subscription patterns and develop data driven recommendations to enhance customer experience and retention.

### Data Sources
##### CUSTOMER Data
The primary dataset used for this analysis is the 'LITA CAPSTONE CUSTOMER DATA SET' provided by The Incubator Hub. This dataset contains information about sales transactions made by the retail storeand it  includes the following key columns:
- Region: The geographical area where the store operates.
- CustomerID : The specific number or tag of a customer
- Product: The list of product available for sale
- SubscriptionType: The date in which a particular order was made.
- SubscriptionStart: The start date of a particular subscription
- SubscriptionEnd: The end date of a particular subscription
- Canceled: This show the packages that was cancelled 
- Revenue: the Amount generated from custkers subscription
- subscription Duration: The time range a customer's active subscroption

### Tool Used
#### Excel
  For Data cleaning
  For Analysis
  
#### Structured Query Language (SQL)
  For Data Querying
  For Analysis
  
#### PowerBI
For Reporting
For Dashboards Presentation

#### Github
For Sharing insight about the project

### Data Cleaning and Preparation
In the initial Preparation phase i performed the following tasks
1. Data loading and inspection
2. Data Cleaning and Formatting
3. Removing duplicates and checking for missing values

### Exploratory Data Analysis
The following questions were answered:
- What are the subscription patterns in the customer data?
- What is the average subscription duration?
- What are the most popular subscription types?
- ⁠What is the total number of customers from each region
- ⁠Which subscription type has the most customers?
- ⁠How many customers canceled their subscription within 6 months?
- ⁠How many customers have subscriptions longer than 12 months?
- ⁠What is the total revenue by subscription type?
- ⁠Which are the top 3 regions by subscription cancellations?
- ⁠What is the total number of active and canceled subscriptions?

### Data Analysis
Here are some of the codes and features utilized to extract insights from the customer data include the following:
#### For SQL
To retrieve the total number of customers from each region. 
```
Select  region, count(distinct Customerid) as total_customers 
from [dbo].[LITA Capstone Dataset]
Group by region
```
To find the most popular subscription type by the number of customers. 
```
Select top 1 subscriptiontype, count(distinct customerid) as total_customers
From [dbo].[LITA Capstone Dataset]
Group by subscriptiontype 
Order by total_customers desc
```
 Find customers who canceled their subscription within 6 months. 
```
Select customerid
From [dbo].[LITA Capstone Dataset]
Where datediff(month, subscriptionstart, subscriptionend) <= 6
```
calculate the average subscription duration for all customers. 
```
Select avg(datediff(day, subscriptionstart, subscriptionend)) as avg_subscription_duration
From [dbo].[LITA Capstone Dataset]
```
find customers with subscriptions longer than 12 months. 
```
Select customerid
From [dbo].[LITA Capstone Dataset]
Where datediff(month, subscriptionstart , subscriptionend) > 12
```
calculate total revenue by subscription type. 
```
Select subscriptiontype,
Sum(revenue) as total_revenue 
From [dbo].[LITA Capstone Dataset]
Group by subscriptiontype
```
Find the top 3 regions by subscription cancellations. 
```
Select top 3 region,
Count(*) as subscriptionend_count
From [dbo].[LITA Capstone Dataset]
Where subscriptionend is null
Group by region
Order by subscriptionend_count desc
```

#### Pivot Summarization
Region by Sum of Revenue
![Screenshot 2024-11-07 235329](https://github.com/user-attachments/assets/ddfe0897-27b4-418a-acb6-40cc71110b4e)

Region by Count of Canceled
![Screenshot 2024-11-07 235423](https://github.com/user-attachments/assets/5351d65c-d038-4e2f-a59e-8f48e8431447)

### Visualization
#### Insight from PowerBI



### Result and Conclusion
The result of the analysis are summarized as follows:
The average customer value is substantial indicating potential for significant revenue growth. Regional customer distribution is relatively even, with East, North, South, and West regions having similar customer counts. Cancellation rate is high, highlighting the need for effective retention strategies. Basic subscription type generates the most revenue followed by Standard and Premium each. Top 10 customers account for significant revenue emphasizing the importance of targeted customer retention.

### Recommendations
Based on the analysis, I recommend the following actions:

Implement targeted retention strategies to reduce high cancellation rates.

Enhance Basic subscription features to maintain competitive edge.

Conduct regular customer feedback surveys to inform retention strategies.

Monitor and analyze cancellation reasons.

Develop tailored retention programs for top 10 customers


### Limitations
To ensure accuracy and reliability of the analysis, i had to remove all zero-value were excluded from the dataset, as they could potentially skew the results and misinterpret true trends and patterns.
