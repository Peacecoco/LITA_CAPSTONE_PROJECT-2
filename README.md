# LITA_CAPSTONE_PROJECT-2

### Table of Content
---
1. [Project Overview](#project-overview)
2. [Introduction](#introduction)
3. [Tools Used](#tools-used)
4. [Data Exploration](#data-exploration)
5. [SQL Queries](#sql-queries)
6. [PowerBI Dashboard](#powerbi-dashboard)
7. [Insights and Recommendations](#insights-and-recommendations)
8. [Conclusion](#conclusion)
9. [Appendices](#appendices)

### Customer Segmentation for a subscription service
---

### Project Overview
---
This project shows the analysis of the customer segmentation for a subscription service. The analysis was carried out by exploring the customer data to uncover key insights such as subscription trends, cancellations, and customer segments.

### Introduction
---
Customer Segmentation for a subscription service, seeks to optimize its customer subscription trends and improve customer subscription patterns. With increasing competition in the market, the customer's management recognizes the need for data-driven decision-making to stay ahead.

### Tools Used
---
This project employs a combination of data exploarion, SQL querying, and data exploration, SQL querying, and data visualization technqiues using:
- Microsoft Excel for data exploration and calculation
- SQL Server for data querying and analysis
- PowerBI for interactive dashboard creation

### Data Exploration
---
- EXCEL ANALYSIS
   - Analysis on customer data using pivot table to find subscription patterns
   - Average subscription duration and identification of the most popular subscription types
   - Create any other interesting reports.

 
### SQL Queries
---
Query 1: Tottal number of customers from each region.
```SQL
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY Region
```
Query 2: Most Popular subscription type by the number of customers.
```SQL
SELECT SubscriptionType, COUNT(CustomerID) AS No_of_Customer
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY SubscriptionType
```
Query 3: Customers who canceled their subscription within 6 months.
```SQL
SELECT CustomerName, Canceled, SubscriptionStart 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE Canceled = 0 AND
MONTH(SubscriptionStart)
BETWEEN 1 AND 6
```
Query 4: Average Subscription duration for all customers
```  SQL
SELECT Count(CustomerID) AS All_Customers, AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) 
AS Average_Subscription_Duration 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE SubscriptionEnd IS NOT NULL
```
Query 5: Customers with subscriptions longer than 12 months.
```SQL
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE DATEDIFF(MONTH, SubscriptionStart,SubscriptionEnd)>=12
```
Query 6: Total revenue by subscription type
```SQL
SELECT SubscriptionType, SUM(Revenue) AS Total_Revenue
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY SubscriptionType

```
QUERY 7: Top 3 regions by subscription cancellations
```SQL
SELECT TOP 3 Region, Canceled 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
```
Query 8: Total number of active and canceled subscriptions
```SQL
SELECT SUM(CASE WHEN Canceled=0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
SUM(CASE WHEN Canceled=1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[LITACAPSTONE CUSTOMER DATA] 
GROUP BY CustomerID
```


### PowerBI Dashboard
---
- Create visualizations for:
   - Customer segmentation by region and subscription type
   - Cancellation rates by subscription type and region
   - Average subscription duration by subscription type
   - Total revenue by subscription counts
   - Active and canceled subscription counts

- Description of visualizations and insights.

### Final Deliverables
---
- A comprehensive PowerBI dashboard showcasing customer segments, cancellations, and subscription trends.
- Accompanied by a report detailing findings and insights fro Excel and SQL analyses.

### Appendices
---
- Capstone Sales Dataset

