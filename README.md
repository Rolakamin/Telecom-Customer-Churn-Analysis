# Telecom Customer Churn Analysis


## Table of Contents

- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Business Objectives](#business-objectives)
- [Problem Statements](#problem-statements)
- [Dataset Overview](#dataset-overview)
- [Data Sources](#data-sources)
- [Data Cleaning and Transformation](#data-cleaning-and-transformation)
- [Data Modelling](#data-modelling)
- [DAX Measures Development](#dax-measures-development)
- [Data Analysis and Visualization](#data-analysis-and-visualization)
- [Findings and Insights](#findings-and-insights)
- [Recommendations](#recommendations)
- [Challenges and Limitations](#challenges-and-limitations)
  


## Introduction

The telecommunications industry is highly competitive, with customers having access to a wide range of service providers. As a result, customer churn, the rate at which customers discontinue their services remains, a critical business challenge for telecom companies.

This project is part of a Maven Analytics challenge and is based on a fictional dataset from Maven Communications, a California-based telecommunications provider. The analysis focuses on understanding customer churn behavior, identifying key drivers of attrition, uncovering meaningful patterns across customer segments, and recommending data-driven actions to improve customer retention.

In this project, I assume the role of a BI Consultant, responsible for translating analytical findings into strategic insights for the Chief Marketing Officer (CMO). These insights are delivered through a concise, one-page Power BI dashboard designed to support executive decision-making.


## Project Overview

This project focuses on analyzing customer churn for Maven Communications. The goal is to understand churn behavior, uncover patterns, and recommend strategies to improve retention.

## Business Objectives

### Main Objective

To help the company improve retention by identifying high-value customers and churn risks.

### Specific Objectives

- Analyze customer data to identify high-value customers
- Calculate churn rates for different customer segments
- Identify the main reasons why customers are leaving
- Determine which customer demographics have the highest churn risk
- Create metrics to measure customer value and churn probability
- Build a dashboard to visualize churn patterns and risks
- Provide actionable recommendations for retention strategies


## Problem Statements

- How many customers joined, stayed, or churned during the last quarter?
- What are the characteristics of customers who churned versus those who stayed?
- What are the main drivers of customer churn?
- Is the company losing high-value customers disproportionately?
- Which customer segments show the highest churn risk?
- Where should retention efforts be focused for maximum impact?


## Dataset Overview

### Primary Dataset: Telecom Customer Churn
- **Records:** 7,043 customer accounts  
- **Time Period:** Q2 2022 (April–June)  
- **Original Columns:** 38  
- **Final Columns:** 41 (after feature engineering)  
- **Categories / Key Features:** Customer demographics, service subscriptions, billing information, contract details, churn status  

### Supporting Dataset: Zip Code Population
- **Records:** 1,671 California zip codes  
- **Purpose:** Geographic analysis and market penetration calculations  
- **Key Features:** Zip code, estimated population  


## Data Sources

The datasets used for this analysis are in CSV format. Details are also available at [Maven Analytics Data Playground](https://www.mavenanalytics.io/data-playground).

**1. Maven Analytics Telecom Customer Churn Dataset**  

The dataset contains customer account information for analysis.  

Download: [telecom_customer_churn.csv](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/telecom_customer_churn.csv)

**2. California Zip Code Population Dataset**  

The dataset contains population estimates for California zip codes.  

Download: [telecom_zipcode_population.csv](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/telecom_zipcode_population.csv)

**3. Data Dictionary**  

The data dictionary defines each column, its data type, and business meaning.  

Download: [telecom_data_dictionary.csv](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/telecom_data_dictionary.csv)


## Data Cleaning and Transformation

### Data Quality Issues Identified and Resolved
- **Negative Monthly Charges:** Identified and corrected negative values by replacing them with $0  
- **Missing Service Data:** Addressed blank fields in phone and internet service columns  
- **Incomplete Churn Information:** Handled null values in churn category and reason fields  
- **Data Type Inconsistencies:** Standardized data types across all columns  

### Feature Engineering
New features were created in Power Query to enhance analytical depth and enable meaningful segmentation:

- **Age Group:** Segmented customers into 19–30, 31–45, 46–60, and 61+

  

 ![Age Group Screenshot](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/age_group.png)
 
  - **Tenure Range:** Grouped tenure into 0–12, 13–24, 25–36, 37–48, 49–60, and 61+ months



 ![Tenure Range Screenshot](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/tenure_range.png)


   
- **Customer Value Tier:** Classified customers based on monthly charges:
  - Low (<$50)  
  - Medium ($50–$80)  
  - High (>$80)
 

![Customer Value Tier Screenshot](    https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/customer_value_tier.png
 )
       

**Screenshots illustrating the Power Query transformations are included to demonstrate the feature engineering process.**


## Data Modeling

### Data Relationships

- Established a one-to-many relationship between the Telecom Customer Churn table and the Zip Code Population table using Zip Code as the primary key.
  
- Applied a single-direction filter flow from the Zip Code Population table to the Customer Churn table to support accurate geographic analysis and market penetration analysis.


**Power BI model view illustrating table relationships is shown below.**


 ![Data Model Screenshot](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/data_model.png)



## DAX Measures Development

This section outlines the key DAX measures created to support churn, retention, financial, and service-level analysis. Each measure is briefly explained to clarify its business meaning, followed by the corresponding DAX formula.

### Customer Count Metrics

**Total Customers**

Represents the total number of customer records in the dataset. This measure serves as the base metric for all rate and percentage calculations.

````
Total Customers = 
COUNTROWS('telecom_customer_churn')
````

**Churned Customers**

Counts the number of customers whose status is marked as -**Churned**- during the quarter.

````
Churned Customers = 
CALCULATE(
    [Total Customers],
    'telecom_customer_churn'[Customer Status] = "Churned"
)
````

**Stayed Customers**

Counts customers who remained with the company during the analysis period.

````
Stayed Customers = 
CALCULATE(
    [Total Customers], 
    'telecom_customer_churn'[Customer Status] = "Stayed"
)
````

**Joined Customers**

Counts new customers who joined the company during the quarter.

````
Joined Customers = 
CALCULATE(
    [Total Customers],
    'telecom_customer_churn'[Customer Status] = "Joined"
)
````

### Churn and Retention Rates

**Churn Rate**

Measures the proportion of customers who churned relative to the total customer base for the period.

````
Churn Rate = 
DIVIDE([Churned Customers], [Total Customers], 0)
````

**Retention Rate**

Measures the proportion of customers who stayed with the company during the quarter.

````
Retention Rate = 
DIVIDE([Stayed Customers], [Total Customers], 0)
````


**Join Rate**

Represents the percentage of new customers acquired relative to the total customer base.

````
Join Rate = 
DIVIDE([Joined Customers], [Total Customers], 0)
````

**High Value Churned**

Counts the number of churned customers classified as High Value based on monthly charges.

````
High Value Churned = 
CALCULATE(
    [Total Customers],
    'telecom_customer_churn'[Customer Status] = "Churned",
    'telecom_customer_churn'[Customer Value Tier] = "High Value"
)
````


**High Value Churn Rate**

Calculates the churn rate specifically for high-value customers, highlighting whether premium customers are leaving at a higher rate.

````
High Value Churn Rate = 
VAR HighValueCustomers = 
    CALCULATE(
        [Total Customers], 
        'telecom_customer_churn'[Customer Value Tier] = "High Value"
    )
VAR HighValueChurned = 
    CALCULATE(
        [Total Customers],
        'telecom_customer_churn'[Customer Status] = "Churned",
        'telecom_customer_churn'[Customer Value Tier] = "High Value"
    )
RETURN
DIVIDE(HighValueChurned, HighValueCustomers, 0)
````


### Customer Behaviour and Tenure Metrics

**Average Tenure (Months)**

Calculates the average number of months customers have remained with the company.

````
Avg Tenure Months = 
AVERAGE('telecom_customer_churn'[Tenure in Months])
````

**Average Tenure of Churned Customers**

Measures how long churned customers stayed before leaving, helping identify early versus long-term churn patterns.

````
Avg Tenure of Churned Customers = 
CALCULATE(
    [Avg Tenure Months],
    'telecom_customer_churn'[Customer Status] = "Churned"
)
````


**New Customer Retention Rate**

Evaluates the retention rate of customers within their first 12 months, highlighting onboarding and early experience effectiveness.

````
New Customer Retention Rate = 
CALCULATE(
    [Retention Rate], 
    'telecom_customer_churn'[Tenure Range] = "0-12 Months"
)
````


### Financial Metrics

**Total Revenue**

Calculates the total revenue generated from all customers in the dataset.

````
Total Revenue = 
SUM('telecom_customer_churn'[Total Revenue])
````

**Average Revenue Per User (ARPU)**

Measures the average revenue generated per customer, a key telecom performance indicator.

````
Average Revenue Per User (ARPU) = 
DIVIDE([Total Revenue], [Total Customers], 0)
````

**Average Monthly Charge**

Calculates the average monthly charge billed to customers.

````
Avg Monthly Charge = 
AVERAGE('telecom_customer_churn'[Monthly Charge])
````


**Revenue Lost to Churn**

Estimates the total revenue lost due to customers who churned during the quarter.

````
Revenue Lost to Churn = 
CALCULATE(
    SUM('telecom_customer_churn'[Total Revenue]),
    'telecom_customer_churn'[Customer Status] = "Churned"
)
````

### Penetration Metrics

**Customers Per Capita**

Measures customer penetration by comparing the number of customers to the population in each zip code.

````
Customers Per Capita = 
DIVIDE(
    [Total Customers],
    SUM('telecom_zipcode_population'[Population]),
    0
)
````

### Service and Product Metrics

**Internet Service Churn Rate**

Calculates the churn rate among customers subscribed to internet services.

````
Internet Service Churn Rate = 
CALCULATE(
    [Churn Rate], 
    'telecom_customer_churn'[Internet Service] = "Yes"
)
````

**Phone Service Churn Rate**

Calculates the churn rate among customers subscribed to phone services.

````
Phone Service Churn Rate = 
CALCULATE(
    [Churn Rate], 
    'telecom_customer_churn'[Phone Service] = "Yes"
)
````




## DAX Measures Development

- **Customer Base Metrics**: Total Customers, Churned Customers, Stayed Customers, Joined Customers

- **Performance Rates**: Churn Rate, Retention Rate, Join Rate, High Value Churn Rate

- **Financial Analytics**: Total Revenue, Revenue Lost to Churn, ARPU, Average Monthly Charge

- **Behavioral Analysis**: Average Tenure Months, New Customer Retention Rate

- **Service Metrics**: Internet Service Churn Rate, Phone Service Churn Rate


## Data Analysis and Visualization

A one-page Power BI dashboard was developed to address key business questions around customer churn, revenue impact, and retention opportunities for Q2 2022. The visuals focus on delivering clear, actionable insights for executive decision-making.

### Key Performance Indicator

Key KPIs summarize overall customer and financial performance:
- **Total Revenue:** $21.37M  
- **Revenue Lost to Churn:** $3.68M  
- **Churn Rate:** 26.54%  
- **High-Value Churn Rate:** 34.11%  
- **Joined Customers:** 454  
- **New Customer Retention:** 31.79%  

These metrics show that churn represents a significant financial risk, particularly among high-value and newly acquired customers.

---

### Customer Churn Distribution

A donut chart shows customer status distribution:
- **Stayed:** 67.02%  
- **Churned:** 26.54%  
- **Joined:** 6.45%  

This confirms that while most customers remain active, churn affects over one-quarter of the customer base.

---

### High-Value Customers and Churn Risk

A pie chart highlights churned customers by value tier:
- **High Value:** 47.9%  
- **Medium Value:** 31.8%  
- **Low Value:** 20.3%  

High-value customers account for nearly half of total churn, indicating disproportionate revenue risk.

---

### Demographic Churn Patterns

A clustered bar chart comparing churned, stayed, and joined customers by age group shows:
- The **61+ age group** has the highest churn volume
- Younger customers demonstrate stronger retention and acquisition performance  

Higher churn among customers aged 61 and above highlights this group as a critical focus area for retention efforts.

---

### Geographic Concentration of Churn

A clustered bar chart displays the **Top 5 Cities by Churned Customers**, ranked by churn rate:
- **San Diego** and **Fallbrook** exhibit exceptionally high churn rates  

This reveals concentrated geographic churn risk and supports targeted, location-based retention efforts.

---

### Drivers of Customer Churn

A bar chart of churn reasons shows that competitive factors dominate:
- Better competitor devices, offers, and data plans account for **approximately 68%** of top churn reasons  

This suggests churn is driven primarily by market competition rather than internal service failures.

---

### Strategic Focus Areas

Based on the analysis, three priority actions are highlighted:
1. **Competitive Response:** Improve device offerings, pricing, and data plans  
2. **Senior Customer Retention:** Simplify plans and enhance support for customers aged 61+  
3. **High-Value Customer Protection:** Proactive retention for customers with monthly charges above $80  

**Geographic Focus:** Immediate attention should be directed toward high-churn cities such as **San Diego** and **Fallbrook**.

---

### Summary

The dashboard consolidates customer, financial, demographic, and geographic insights into a single, executive-ready view. It identifies high-risk segments, key churn drivers, and priority intervention areas, enabling data-driven retention strategies aligned with business objectives.

---

### Executive Dashboard Snapshot

The screenshot below presents the complete one-page Power BI dashboard, designed to provide an at-a-glance view of customer churn performance, revenue exposure, and priority risk areas for Q2 2022.

![Telecom Customer Churn Dashboard](https://github.com/Rolakamin/Telecom-Customer-Churn-Analysis/blob/main/telecoms_customer_churn_dashboard.png)

---

### Interactive Dashboard (Power BI Service)

An interactive version of the dashboard is available on Power BI Service, enabling deeper exploration of churn patterns across customer segments and locations.  

🔗 [Explore the Power BI dashboard](https://app.powerbi.com/groups/me/reports/83daed16-935b-4511-815a-79346a773801/b3dea5a26a46180d3c70?experience=power-bi)



## Findings and Insights

- Customer churn represents a significant financial risk, with a churn rate of 26.54% and over $3.68M in revenue lost during Q2 2022.

- High-value customers are disproportionately affected by churn, accounting for nearly 48% of all churned customers, indicating that revenue loss is driven not just by volume, but by the exit of customers with higher monthly charges.

- Senior customers (61+) show the highest churn volumes, suggesting that existing products, pricing structures, or support experiences may not be well-aligned with the needs of older customers.

- Churn is geographically concentrated, with San Diego and Fallbrook exhibiting exceptionally high churn rates compared to other cities, highlighting clear opportunities for location-specific retention initiatives.

- Competitive pressures are the primary drivers of churn, as competitor-related issues (better devices, pricing, and data plans) account for approximately 68% of the top churn reasons, outweighing service or support-related factors.

- New customer retention remains weak, with fewer than one-third of newly joined customers retained, indicating gaps in onboarding, early engagement, or value communication during the first year of the customer lifecycle.

## Recommendations

Based on the analysis, the following actions are recommended to reduce churn and protect revenue:

- Respond to competitive pressure: Improve device offerings, pricing, and data plan flexibility, and introduce targeted incentives to counter competitor-driven churn.

- Protect high-value customers: Proactively retain customers with monthly charges above $80 through loyalty benefits, priority support, and early churn intervention.

- Improve retention among senior customers (61+): Simplify plans and billing, enhance communication clarity, and provide dedicated support to address the highest-risk age segment.

- Target high-churn locations: Focus retention efforts in San Diego and Fallbrook, using localized campaigns and location-specific analysis before scaling.

- Strengthen early customer retention: Improve onboarding and engagement within the first 90 days through incentives, follow-ups, and early churn monitoring.


## Challenges and Limitations

**Data Constraints**

- **Single-quarter analysis (Q2 2022)**: Only one quarter of data was available, so trends over time cannot be observed, limiting insights on whether churn is increasing or decreasing.

- **Missing satisfaction and service quality metrics**: Customer happiness and service performance data were not included, which limits understanding of why customers leave.

- **Self-reported churn reasons**: Customers provided their own reasons for leaving, which may be biased or incomplete, potentially affecting the accuracy of churn driver analysis.
  

**Analytical Limitations**

- **Correlation, not causation**: Observed patterns, such as higher churn among senior customers, show a relationship but do not prove that age directly causes churn. Other factors (like plan complexity or device preferences) could be influencing their behavior. Recommendations are based on these insights, but they do not guarantee outcomes.

- **Zip code-level geographic analysis**: Analysis is limited to zip codes, which may mask local neighborhood variations in churn.

- **No cost data**: Without detailed costs of retention efforts or customer acquisition, exact financial impact or ROI of interventions cannot be calculated.
















