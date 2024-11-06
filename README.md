# LITA-CAPSTONE-PROJECT-CUSTOMER-DATA

# LITA-CAPSTONE-PROJECT-SALES-DATA

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
This analysis project aim to generates insight into the sales performance of of a retails store over the past years by analysing the variuos parameters in the data received.
We seek to gather enough insight to make reasonable decisions which then enable us to tell a compelling stories around our data from the insight gotten and to know the best performance from our data uilizing Excel, SQL, and Power BI, the analysis will identify top-selling products, regional trends and monthly Sales pattern. 
By analyzing various aspect of the sales data, this project aims to uncover trends, make data-driven recommedations, and gain a deeper understanding of the company's performance, ultimately designning an interactive Power BI dashboard for stakeholder decision making.

### Data Sources
##### Sales Data
The primary dataset used for this analysis is the 'LITA CAPSTONE DATASET' provided by The Incubator Hub. This dataset contains information about sales transactions made by the retail storeand it  includes the following key columns:
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
Data loading and inspection
Handling Missing Variables
Data Cleaning and Formatting
Removing Duplicates

### Exploratory Data Analysis
- retrieve the total number of customers from each region.
- find the most popular subscription type by the number of customers.
- find customers who canceled their subscription within 6 months.
- calculate the average subscription duration for all customers.
- find customers with subscriptions longer than 12 months.
- calculate total revenue by subscription type.
- find the top 3 regions by subscription cancellations.
- find the total number of active and canceled subscriptions. 

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
##### Total Sales by Product

##### Total Sales by Region


##### Total Sales by Month


##### Region by Product, Total Sales and Quantity



### Visualization
#### Insight from PowerBI



### Result and Conclusion
The result of the analysis are summarized as follows:

The Retail Store sales fluctuate throughout the year, peaking consistently in February. In sales and revenue Shoes and the South region are the best performing. Shirts has the highest average sales while South region alsp boasts the highest average sales. Notably, 2023 sales exceeded 2024 sales by 9.9%, although 2024 is yet to conclude.

### Recommendations
Based on the sales analysis and to capitalize on the insight and findings, I recommend the following strategic actions:

Invest in targeted marketing and promotions to leverage the February sales peak,and maximizing revenue potential.
Prioritize promotions for Shoes and Shirts, ensuring these top-selling products receive adequate attention.
Concentrate marketing efforts on the high-performing South region to further boost sales.
Explore targeted campaigns and opportunities to grow sales in the underperforming west region.
Implement a customer segmentation strategy to effectively target high lifetime value customers

### Limitations
Notable limitations were minimized due to the dataset's cleanliness as no null or blank columns were present, ensuring data integrity However, removing duplicates from the dataset initially may have potentially impacted the accuracy of the analysis.
