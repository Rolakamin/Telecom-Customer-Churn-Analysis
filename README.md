# Telecom Customer Churn Analysis

## Introduction

The telecommunications industry is highly competitive, with customers having access to a wide range of service providers. As a result, customer churn, the rate at which customers discontinue their services remains a critical business challenge for telecom companies.

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

  
- **Tenure Range:** Grouped tenure into 0–12, 13–24, 25–36, 37–48, 49–60, and 61+ months

   
- **Customer Value Tier:** Classified customers based on monthly charges:
  - Low (<$50)  
  - Medium ($50–$80)  
  - High (>$80)
 

    

Screenshots illustrating the Power Query transformations are included to demonstrate the feature engineering process.


## Data Modeling

**Data Relationships**

- Established primary relationship between customer churn and zip code population tables using Zip Code as key

## DAX Measures Development

- **Customer Base Metrics**: Total Customers, Churned Customers, Stayed Customers, Joined Customers

- **Performance Rates**: Churn Rate, Retention Rate, Join Rate, High Value Churn Rate

- **Financial Analytics**: Total Revenue, Revenue Lost to Churn, ARPU, Average Monthly Charge

- **Behavioral Analysis**: Average Tenure Months, New Customer Retention Rate

- **Service Metrics**: Internet Service Churn Rate, Phone Service Churn Rate

## Data Analysis and Visualization


## Findings and Insights

Critical Business Discoveries

- High-Value Customer Attrition: 34.11% churn rate among high-value segments versus 26.54% company average

- Competitive Vulnerability: 68% of primary churn reasons attributed to competitive factors including better devices, offers, and data plans

- Demographic Trends: Customers aged 61+ demonstrate highest churn volume with 606 customers lost

- Geographic Concentration: Southern California regions, particularly San Diego, Fallbrook, and Temecula, show churn rates exceeding 57%

- Retention Gaps: New customer retention critically low at 31.79%, indicating onboarding process deficiencies

- Service Performance: Internet service subscribers churn at 31.83% compared to 26.71% for phone service customers

## Recommendations

Strategic Initiatives
Competitive Response Program
Implement competitive offer matching for devices and data plans

Establish continuous competitive intelligence monitoring

Develop rapid response capabilities for competitive threats

Customer Segment Protection
Create specialized retention programs for high-value customers

Design simplified service bundles for senior customer segments

Implement proactive retention outreach for at-risk customers

Operational Improvements
Enhance new customer onboarding experience

Develop geographic-specific retention strategies for high-churn areas

Optimize service bundles based on churn analysis findings


## Challenges and Limitations

Data Constraints
Limited to single quarter analysis without historical trend data

Absence of customer satisfaction and service quality metrics

Self-reported churn reasons potentially subject to response bias

Analytical Limitations
Inability to establish causal relationships due to correlational nature

Geographic analysis constrained to zip code level granularity

Missing cost data prevents comprehensive ROI calculations


References
Data Sources
Maven Analytics Telecom Customer Churn Dataset

California Zip Code Population Estimates

Technical Documentation
Microsoft Power BI Official Documentation

DAX Function Reference Guide

Data Visualization Best Practices

Industry Resources
Telecommunications Industry Churn Benchmarks

Customer Retention Strategy Frameworks

Executive Dashboard Design Principle









**Maven Telecommunications** is facing customer retention challenges and needs to understand the underlying causes and patterns of churn in order to develop effective customer retention strategies.

This project seeks to answer the following key business questions:

- How many customers joined the company during the last quarter?

- What is the profile of customers who churned, joined, or stayed? How are they different?

- What are the main drivers of customer churn?

- Is the company losing high-value customers? If so, how can they be retained?

- What patterns can be identified based on customer tenure, service usage, and billing?

- Are certain customer segments or demographics more likely to churn than others?

- How can the company use data to make proactive, insight-driven retention decisions?

## Data Overview




