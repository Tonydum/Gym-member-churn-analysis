# Gym Member Churn Analysis

## Table of Contents

- [Project Background](#project-background)
- [Executive Summary](#executive-summary)
- [Objective](#objective)
- [Key Metrics Analyzed](#key-metrics-analyzed)
- [Technologies Used](#technologies-used)
- [Dataset](#dataset)
- [Analysis Process](#analysis-process)
  - [Data Cleaning](#data-cleaning)
  - [Data Transformation](#data-transformation)
  - [DAX Calculations](#dax-calculations)
- [Visualization](#visualization)
- [Key Insights](#key-insights)
- [Dashboard](#dashboard)
- [Recommendations](#recommendations)

## Project Background

As a data analyst, I undertook this project to address a critical challenge faced by gym management: understanding and mitigating member churn. In the fitness industry, retaining members is as important as acquiring new ones, given the high competition and operational costs. The goal of this project was to explore factors influencing churn, segment members based on risk, and provide actionable insights to improve retention and satisfaction.

## Executive Summary

This project explores key drivers of gym member churn, leveraging Power BI and DAX to analyze metrics like contract period, class frequency, lifetime, additional charges, and proximity to the gym. A comprehensive dashboard was created to visualize these factors, highlighting trends such as:

- Churn by Contract Period: 42% churn for 1-month contracts, with minimal churn (2%) for 6-12 month contracts.

- Churn by Lifetime: Members with less than 3 months of membership have a churn rate of 42%.

- Churn by Age: Younger members (18-25 years) churn the most (66%), while older members (36-41 years) churn the least (9%).

- Churn by Class Frequency: Medium and low attendance lead to higher churn rates (37% and 35%), while high attendance correlates with lower churn (14%).

- Churn by Additional Charges: Low Spenders churn at 36%, while High Spenders churn at only 18%.

Based on these findings, actionable recommendations were developed to target high-risk segments and improve member retention.

## Objective

The primary objective of this project was to:

1. Identify the key factors contributing to member churn.

2. Segment members into risk categories for targeted interventions.

3. Provide actionable insights to improve member retention and satisfaction.

## Key Metrics Analyzed

Total Members: The total number of members in the dataset.

Active Members: Members who have not churned.

Churned Members: Members who have churned.

Churn Rate: Percentage of churned members relative to total members.

Average Additional Charges: Average spending on additional services per member.

Churn Segmentation: Analysis by age, contract period, lifetime, class frequency, and additional charges.

## Technologies Used

To analyze the data and create the dashboard, I used:

Power BI: For data visualization and dashboard creation.

DAX (Data Analysis Expressions): For calculated columns and measures.

CSV File: The source dataset for analysis.

## Dataset

### Overview

The dataset consisted of gym membership information, including demographic, behavioral, and transactional data. Key columns included:

Demographics: Gender, Age

Behavioral: Near_Location, Partner, Promo_friends, Avg_class_frequency_total, Avg_additional_charges_total

Contract Details: Contract_period, Lifetime, Month_to_end_contract

Churn Details: Churn, Churn_label

## Analysis Process

### Data Cleaning

I started by cleaning the dataset to ensure data quality:

Removed duplicate rows and handled missing values.

Standardized column names for consistency.

Validated data ranges for numerical fields to ensure accuracy.

### Data Transformation

To better analyze the data, I created new categories and measures using DAX:

AgeCategory: Grouped members into age ranges (e.g., 18-25 years).

ContractPeriodCategory: Categorized contract periods into "1 month," "1-6 months," and "6-12 months."

AdditionalChargesCategory: Classified members as Low, Medium, or High Spenders based on additional charges.

ClassFrequencyCategory: Segmented class attendance into Low, Medium, and High Frequency.

LifetimeCategory: Categorized membership lifetimes.

LocationCategory: Grouped members as "Lives Near Gym" or "Lives Far from Gym."

### DAX Calculations

I utilized DAX to create measures and calculated columns:

#### Measures:

Total Members: COUNTROWS(gym_churn)

Active Members: CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "No")

Churned Members: CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "Yes")

Churn Rate: gym_churn[Churned Members] / gym_churn[Total Members]

Avg. Additional Charges: AVERAGE(gym_churn[Avg_additional_charges_total])

#### Calculated Columns:

AdditionalChargesCategory: Categorized spending as Low, Medium, or High Spenders.

AgeCategory: Grouped members into age brackets.

ChurnRiskCategory: Segmented members into High, Medium, and Low Risk based on contract period, location, and attendance.

ClassFrequencyCategory: Segmented attendance frequency into Low, Medium, and High.

ContractPeriodCategory: Grouped contract periods into ranges.

LifetimeCategory: Categorized membership duration.

LocationCategory: Classified members by proximity to the gym.

## Visualization

The dashboard includes:

KPIs: Displaying Total Members, Active Members, Churned Members, Churn Rate, and Avg. Additional Charges.

Pie Chart: Visualizing churn by gender.

Bar Charts:

Churn by Contract Period.

Churn by Lifetime.

Churn by Age.

Churn by Class Frequency.

Churn by Additional Charges.

Filters: Gender and Location filters for interactive analysis.

## Key Insights

Churn by Contract Period:

42% churn for 1-month contracts highlights high risk among short-term members.

Longer contracts (6-12 months) have minimal churn (2%).

Churn by Lifetime:

Members with less than 3 months of membership have a churn rate of 42%.

Churn by Age:

Younger members (18-25 years) churn the most (66%), while older members (36-41 years) churn the least (9%).

Churn by Class Frequency:

Medium and low attendance lead to higher churn rates (37% and 35%).

High attendance correlates with lower churn (14%).

Churn by Additional Charges:

Low Spenders have the highest churn rate (36%), while High Spenders churn at 18%.

## Dashboard

![image](https://github.com/user-attachments/assets/928f9cf2-9eed-4e36-8526-649ccea128fe)


## Recommendations

Promote Long-Term Contracts:

Offer discounts or loyalty rewards for 6-12 month memberships.

Engage New Members:

Focus on onboarding programs and personalized fitness plans during the first three months.

Target Younger Members:

Implement youth-oriented campaigns and social activities to retain members aged 18-25.

Encourage Class Participation:

Introduce rewards for frequent class attendance to boost engagement.

Upsell Additional Services:

Promote personal training and premium services to reduce churn among low spenders.

Segment and Target:

Use churn risk categories to develop retention strategies for high-risk members.

