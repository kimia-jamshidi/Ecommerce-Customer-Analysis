# Data Understanding Report

## Dataset Overview

The dataset contains **17,049 e-commerce transactions** and **18 features** related to customer demographics, purchasing behavior, transaction details, and website interaction metrics.

### Dataset Dimensions

* Rows (Transactions): 17,049
* Columns (Features): 18

### Available Features

* Order_ID
* Customer_ID
* Date
* Age
* Gender
* City
* Product_Category
* Unit_Price
* Quantity
* Discount_Amount
* Total_Amount
* Payment_Method
* Device_Type
* Session_Duration_Minutes
* Pages_Viewed
* Is_Returning_Customer
* Delivery_Time_Days
* Customer_Rating

---

## Data Quality Assessment

### Missing Values

No missing values were detected in any column of the dataset.

### Data Types

The dataset contains a mixture of:

* Numerical variables
* Categorical variables
* Boolean variables

The `Date` column is currently stored as an object and will be converted to a datetime format during the data cleaning phase.
The dataset contains e-commerce transactions spanning from January 2023 to March 2024, covering approximately 15 months of customer purchasing activity.
---

## Customer Overview

The dataset contains:

* 5,000 unique customers
* 17,049 unique orders

This indicates that customers made multiple purchases on average, providing a suitable basis for customer behavior analysis.

Average orders per customer:

17,049 / 5,000 ≈ 3.4 orders

---

## Gender Distribution

Customer distribution by gender:

* Female: 8,613
* Male: 8,176
* Other: 260

The gender distribution is relatively balanced between male and female customers, while the "Other" category represents a small portion of the customer base.

---

## Product Category Distribution

The dataset includes eight product categories:

* Sports
* Beauty
* Books
* Food
* Toys
* Electronics
* Home & Garden
* Fashion

The category distribution appears relatively balanced, reducing the risk of severe category imbalance during analysis.

---

## Payment Method Analysis

Most transactions were completed using digital payment methods.

Distribution:

* Credit Card: 6,801
* Debit Card: 4,321
* Digital Wallet: 3,276
* Bank Transfer: 1,763
* Cash on Delivery: 888

Credit cards represent the most frequently used payment method.

---

## Device Usage Analysis

Customers primarily use mobile devices for shopping.

Distribution:

* Mobile: 9,543
* Desktop: 5,845
* Tablet: 1,661

This suggests that mobile optimization may play an important role in customer engagement and sales performance.

---

## Returning Customer Analysis

Returning customers account for the majority of transactions.

Distribution:

* Returning Customers: 15,039
* New Customers: 2,010

Approximately 88% of transactions come from returning customers, indicating a strong level of customer retention within the dataset.

---

## Numerical Feature Observations

### Total Amount

Key statistics:

* Mean: 1,277.44
* Median: 455.85
* Maximum: 37,852.05

The large difference between mean and median suggests the presence of high-value transactions and a right-skewed distribution.

### Customer Age

* Minimum: 18
* Maximum: 75
* Mean: 34.95

The customer base primarily consists of adults in economically active age groups.

---

## Initial Business Insights

Based on the preliminary exploration, the following business questions will be investigated in later phases:

1. Which product categories generate the highest revenue?
2. Which customer segments contribute most to total sales?
3. Do returning customers spend more than new customers?
4. Which cities generate the highest revenue?
5. Does device type influence purchasing behavior?
6. What customer groups should be targeted for marketing campaigns?

These questions will guide the subsequent stages of data cleaning, exploratory analysis, customer segmentation, and predictive modeling.


## Duplicate Records Assessment

A duplicate record check was performed on the transaction dataset.

Result:

* Duplicate Rows: 0

This indicates that each transaction record is unique and no duplicated orders were detected in the dataset.

The absence of duplicate records reduces the risk of biased aggregations and inaccurate business insights during later stages of the analysis.

## Customer Activity Assessment

The dataset contains 5,000 unique customers and 17,049 transactions.

A duplicate check on the Customer_ID column resulted in 12,049 repeated customer identifiers. This behavior is expected because a single customer may place multiple orders over time.

The presence of repeat purchases makes the dataset suitable for customer behavior analysis, customer segmentation, and loyalty assessment.


Current Project Status

So far we have found:

✅ Missing Value = 0

✅ Duplicate Order = 0

✅ Revenue formula is valid

✅ We have 5000 active customers

✅ Customers are repeat buyers

✅ Data is suitable for Segmentation

✅ Data is suitable for Revenue Analysis




---



# Data Cleaning Report

## Date Conversion

The `Date` column was successfully converted from object format to `datetime64[ns]`.

This transformation enables time-based analysis such as:

* Monthly sales trends
* Yearly comparisons
* Seasonal purchasing patterns
* Revenue growth analysis

---

## Feature Engineering

Two new temporal features were created:

### Month

Extracted from the transaction date to support monthly trend analysis.

### Year

Extracted from the transaction date to support yearly aggregation and comparison.

---

## Data Quality Status

After the transformation:

* Missing Values: 0
* Duplicate Orders: 0
* Invalid Date Values: 0

The dataset is now prepared for exploratory data analysis (EDA) and business insight generation.





------------------------------------------------------------------------------------------------

# EDA Report


## Revenue by Product Category (EDA Insight)

An initial exploratory analysis was conducted to identify the most profitable product categories.

The total revenue was aggregated by product category using transaction-level data.

Key Finding:
The analysis shows that revenue is not evenly distributed across categories. Some product categories contribute significantly more to total revenue than others.

This insight can help the business optimize marketing budgets and focus on high-performing categories to maximize revenue.

### Revenue by Product Category
Objective

The objective of this analysis was to identify which product categories generate the highest revenue for the business.

Methodology

Total revenue was aggregated by product category using the Total_Amount variable.

Findings
Category	Revenue
Electronics	          10,481,897
Home & Garden	      4,023,904
Sports	              3,205,087
Fashion	              1,577,036
Toys	              1,014,238
Beauty	               694,437
Food	               422,055
Books	               360,399

Key Insights
- Electronics is the highest revenue-generating category.
- Electronics contributes approximately 48% of total revenue.
- Home & Garden and Sports are the second and third strongest categories.
- Books and Food generate the lowest revenue among all categories.


Business Recommendation
The business should prioritize marketing campaigns and inventory management for the Electronics category because it represents the largest share of total revenue.

Additionally, further investigation should be conducted to determine whether low-performing categories such as Books and Food require strategic improvements or serve niche customer segments.

---

### Order Volume vs Revenue Analysis

Objective
To determine whether the high revenue generated by the Electronics category is driven by a larger number of transactions or by higher-value purchases.

Findings
The transaction count across product categories is relatively balanced, ranging between approximately 2,000 and 2,250 orders per category.

Despite having a similar number of transactions, Electronics generates significantly more revenue than all other categories.

Further analysis of average order value reveals that:

Electronics: 5,053
Home & Garden: 1,953
Sports: 1,426
Books: 163
Key Insight

The Electronics category achieves the highest revenue primarily because customers spend considerably more per transaction.

Revenue leadership is driven by transaction value rather than transaction volume.


Business Recommendation
The company should prioritize customer retention and premium-product marketing strategies within the Electronics category, as small increases in Electronics sales can have a disproportionately large impact on total revenue.


---

### Revenue by City

Objective
To identify which cities generate the highest revenue and contribute most to overall business performance.

Findings
The revenue distribution is concentrated in a small number of cities.

Top revenue-generating cities:

City	      Revenue
Istanbul	5.65M
Ankara	        3.05M
Izmir	        2.65M


Key Insight
Istanbul is the most valuable market, generating approximately 26% of total company revenue.

The top three cities contribute a significant portion of overall sales, indicating that business performance is highly concentrated geographically.

Business Recommendation
Marketing campaigns, inventory allocation, and customer retention strategies should prioritize Istanbul due to its substantial contribution to total revenue.

---

### Revenue vs Average Order Value by City

Objective
To determine whether high-revenue cities generate more revenue because of higher transaction volume or because customers spend more per order.

Findings
While Istanbul generates the highest total revenue, it does not have the highest average order value.


Average order value rankings show:

City	Average Order Value
Bursa	        1346
Antalya	        1334
Gaziantep	1330

Key Insight
Istanbul's revenue leadership is primarily driven by transaction volume rather than customer spending per transaction.

Bursa demonstrates the highest average order value, indicating that customers in Bursa spend more per purchase on average.

Business Recommendation
Different strategies should be applied across cities:

- Istanbul: focus on customer acquisition and retention due to high transaction volume.

- Bursa: focus on premium product offerings and upselling opportunities due to higher spending per transaction.

----------
### Returning vs New Customers

Key Findings
- Returning customers generated approximately 19.2 million in revenue.
- New customers generated approximately 2.6 million in revenue.
- Average order values were very similar between the two groups.
- Revenue differences are primarily driven by purchase frequency rather than spending per transaction.

Business Insight
Customer retention appears to be a major driver of business revenue. The company benefits more from encouraging repeat purchases than from increasing average order value among existing customers.

---
### Revenue by Gender

Objective
To evaluate purchasing behavior across customer gender groups.

Findings
- Female customers generated the highest total revenue.
- Female and male customers exhibit very similar average order values.
- The higher revenue generated by female customers is primarily explained by a higher number of transactions.
- The "Other" category shows the highest average order value but contains a relatively small number of observations.

Key Insight
Revenue differences across genders are mainly driven by transaction volume rather than spending behavior per order.

Business Recommendation
Marketing efforts can be designed for both male and female customer groups, as their average spending patterns are highly similar.


---
### Revenue by Device Type

Objective
To understand how different device types contribute to business revenue.

Findings
- Mobile devices generate the highest total revenue.
- Desktop users exhibit the highest average order value.
- Tablet users contribute the smallest share of revenue.


Key Insight
Mobile dominates revenue because of transaction volume, while Desktop users spend slightly more per transaction.


Business Recommendation
The business should continue optimizing the mobile shopping experience due to its large revenue contribution, while also investigating opportunities to increase traffic to desktop channels where customer spending per order is higher.

---

## Customer Segmentaion

#### Objective

The goal of this notebook is to identify different customer groups based on their purchasing behavior using RFM (Recency, Frequency, Monetary) analysis and clustering techniques.

This analysis will help the business understand which customers are the most valuable and which customers require retention strategies.

---

## Building Customer-Level RFM Dataset

### Objective
Transform transaction-level data into customer-level metrics for segmentation.

### Metrics Created

- Recency: Number of days since the customer's last purchase.
- Frequency: Total number of orders placed by the customer.
- Monetary: Total revenue generated by the customer.

### Result
A customer-level dataset containing 5,000 unique customers was created.

### Business Value
The RFM dataset enables customer segmentation, customer value analysis, retention strategy development, and targeted marketing campaigns.


---

## RFM Summary Statistics

### Frequency
- Average customer placed 3.4 orders.
- Most customers placed between 2 and 5 orders.
- Maximum observed frequency was 10 orders.

### Monetary
- Average customer spending was 4,355.
- Median spending was 2,494.
- Large gap between mean and median indicates the presence of high-value customers.

### Recency
- Average recency was 126 days.
- Some customers purchased very recently, while others have been inactive for over 450 days.

### Key Insight
Customer value distribution is highly uneven. A relatively small group of customers appears to generate a disproportionately large share of total revenue.

---

### Distribution Analysis

#### Frequency
Frequency distribution is positively skewed, indicating that most customers place a small number of orders while a smaller group purchases more frequently.

#### Monetary
Monetary value shows strong positive skewness. A small number of customers contribute disproportionately high revenue, suggesting the presence of high-value customer segments.

#### Recency
Recency is positively skewed, indicating a mix of recently active customers and long-inactive customers.

#### Key Business Insight
Customer behavior is highly heterogeneous. The business appears to rely on a relatively small segment of high-value customers who generate a significant share of total revenue.


---

## Pareto Analysis

### Objective
Determine whether revenue is concentrated among a small group of customers.

### Finding
The top 20% of customers generate approximately 58.6% of total revenue.

### Key Insight
Revenue is not evenly distributed across customers. A relatively small segment of customers contributes the majority of business revenue.

### Business Recommendation
Prioritize retention strategies, loyalty programs, and personalized marketing campaigns for high-value customers.


---

### Objective

The objective of this step was to evaluate customer value using the RFM (Recency, Frequency, Monetary) framework. Each customer was assigned a score from 1 to 5 for Recency, Frequency, and Monetary metrics, allowing the identification of high-value and low-value customer groups.

### Findings
RFM Score Distribution
Minimum RFM Score: 3
Maximum RFM Score: 15
Median RFM Score: 9
Average RFM Score: 9.0

The score distribution indicates a balanced customer base with customers spread across different value levels.

Best Customers (RFM Code = 555)

Customers with an RFM code of 555 represent the most valuable segment.

#### Characteristics:

Purchased recently
Purchase frequently
Generate high revenue

A total of 226 customers belong to this group.

These customers are ideal candidates for loyalty programs, VIP campaigns, and personalized marketing strategies.

Lowest-Value Customers (RFM Code = 111)

Customers with an RFM code of 111 represent the weakest customer segment.

##### Characteristics:

Have not purchased recently
Purchase infrequently
Generate low revenue

A total of 292 customers belong to this group.

These customers may require re-engagement campaigns or can be considered at high risk of churn.

#### RFM Methodology Insight

During Frequency scoring, direct quantile binning (qcut) generated duplicate bin edge errors due to the large number of repeated frequency values.

To address this issue, customer frequencies were first ranked and then divided into quantiles. This approach ensured a balanced and statistically valid segmentation process.

#### Business Insight

The RFM framework successfully transforms raw transaction data into actionable customer intelligence. Instead of treating all customers equally, the business can prioritize marketing efforts based on customer value and engagement level.

This segmentation will be used in the next step to create customer groups such as:

Champions
Loyal Customers
Potential Loyalists
At Risk Customers
Lost Customers

and generate targeted business recommendations for each segment.

---

# 📌 Customer Segmentation Summary

In this section, customers were segmented using the **RFM (Recency, Frequency, Monetary)** framework. Rather than relying solely on predefined templates, the segmentation rules were refined to better reflect the customer lifecycle and business objectives.

The final customer segments are:

* **Champions:** Recent, frequent, and high-value customers. They represent the company's most valuable customer group.
* **Loyal Customers:** Customers who purchase regularly and maintain a strong relationship with the business.
* **Potential Loyalists:** Customers who have shown promising purchasing behavior and have the potential to become loyal customers with appropriate engagement.
* **New Customers:** Recently acquired customers with limited purchase history who require nurturing.
* **Cannot Lose Them:** High-value customers who have become inactive and require immediate retention efforts.
* **At Risk:** Customers who previously engaged with the business but have recently reduced their activity and may churn.
* **Hibernating:** Customers with low recent activity who still have potential to be reactivated through targeted marketing campaigns.
* **Lost:** Customers who have not purchased for a long period and exhibit very low engagement, indicating a low probability of returning.

This segmentation provides a solid foundation for customer analysis and enables the development of personalized marketing strategies, customer retention campaigns, and business decision-making based on customer value and behavior.
