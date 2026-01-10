# Telecom Customer Churn Analysis

## Introduction

The telecom industry is highly competitive due to the wide range of service providers available to consumers. One of the major challenges faced by telecom companies is customer churn, which is the rate at which customers discontinue their services. 

This project is part of a Maven Analytics challenge and is based on a fictional dataset from Maven Communications, a California-based telecommunications company. The goal is to analyze churn behavior, uncover key drivers behind customer attrition, identify patterns, and recommend targeted actions to improve customer retention.

In this project, I assume the role of a BI Consultant, tasked with presenting findings and strategic insights to the Chief Marketing Officer (CMO) in the form of a concise, one-page Power BI dashboard.

## Project Overview

## Business Objectives

### Main Objective: 
To help the company improve retention by identifying high value customers and churn risks.

### Specific Objectives:

- Analyze customer data to identify high-value customers

- Calculate churn rates for different customer segments

- Identify the main reasons why customers are leaving

- Determine which customer demographics have the highest churn risk

- Create metrics to measure customer value and churn probability

- Build a dashboard to visualize churn patterns and risks

- Provide actionable recommendations for retention strategies

## Problem Statements

- How many customers joined, stayed, or churned during the last quarter, and what are the corresponding rates?
- What are the demographic and behavioral characteristics of customers who churned versus those who stayed or joined? Are there significant differences in age, tenure, or value tiers?
- What are the primary reasons customers are leaving the company, and which categories account for the majority of churn?
- Is the company losing high-value customers at a disproportionate rate, and what is the revenue impact of this attrition?
- Do certain services like internet or phone have higher churn rates, and how do service bundles affect customer retention?
- Are there specific cities or geographic areas with significantly higher churn rates that require targeted retention efforts?
- How effective is the company at retaining new customers, and what is the first-year retention rate?

  
PROBLEM STATEMENTS
- How many customers joined, stayed, or churned during the last quarter?

- What are the characteristics of customers who churned versus those who stayed?

- What are the main drivers of customer churn?

- Is the company losing high-value customers disproportionately?

- Which customer segments show the highest churn risk?

- Where should retention efforts be focused for maximum impact


## Dataset Overview

Original Raw Data Structure

Total Columns: 38 columns in the original telecom_customer_churn dataset

Total Rows: 7,043 customer records

Supporting Dataset: telecom_zipcode_population with 2 columns

After Data Transformation
Final Columns: 41 columns (added 3 new columns through feature engineering)

**Feature Engineering is the process of creating new columns (features) from existing raw data to make it more useful for analysis and machine learning.**

New Columns: Age Group, Tenure Range, Customer Value Tier
 
### Dataset Details

**Primary Dataset**: Telecom Customer Churn

**Records**: 7,043 customer accounts

**Time Period**: Q2 2022 (April - June)

**Features**: 41 columns after data transformation

**Categories**: Customer demographics, service subscriptions, billing information, contract details, churn status


**Supporting Dataset**: Zip Code Population

**Records**: 1,671 California zip codes

**Purpose**: Geographic analysis and market penetration calculations

**Features**: Zip code, population estimates

## Data Sources

Maven Analytics Challenge Dataset

California Zip Code Demographic Data

Dataset Download Link

[Insert dataset download link here when available]

## Data Cleaning and Transformation

**Data Quality Issues Identified and Resolved**

- Negative Monthly Charges: Identified and corrected negative values by replacing with $0

- Missing Service Data: Addressed blank fields in phone and internet service columns

- Incomplete Churn Information: Handled null values in churn category and reason fields

- Data Type Inconsistencies: Standardized data types across all columns

### Feature Engineering
Age Segmentation: Created customer age groups (19-30, 31-45, 46-60, 61+)

Tenure Categorization: Developed tenure ranges in months (0-12, 13-24, 25-36, 37-48, 49-60, 61+)

Customer Value Classification: Established value tiers based on monthly spending (Low: <$50, Medium: $50-80, High: >$80)

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




