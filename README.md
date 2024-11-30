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

1. Total Members: The total number of members in the dataset.

2. Active Members: Members who have not churned.

3. Churned Members: Members who have churned.

4. Churn Rate: Percentage of churned members relative to total members.

5. Average Additional Charges: Average spending on additional services per member.

6. Churn Segmentation: Analysis by age, contract period, lifetime, class frequency, and additional charges.

## Technologies Used

To analyze the data and create the dashboard, I used:

- Power BI: For data visualization and dashboard creation.

- DAX (Data Analysis Expressions): For calculated columns and measures.

- CSV File: The source dataset for analysis.

## Dataset

### Overview

The dataset consisted of gym membership information, including demographic, behavioral, and transactional data. Key columns included:

- Demographics: Gender, Age

- Behavioral: Near_Location, Partner, Promo_friends, Avg_class_frequency_total, Avg_additional_charges_total

- Contract Details: Contract_period, Lifetime, Month_to_end_contract

- Churn Details: Churn, Churn_label

## Analysis Process

### Data Cleaning

I started by cleaning the dataset to ensure data quality:

1. Removed duplicate rows and handled missing values.

2. Standardized column names for consistency.

3. Validated data ranges for numerical fields to ensure accuracy.

### Data Transformation

To better analyze the data, I created new categories and measures using DAX:

- AgeCategory: Grouped members into age ranges (e.g., 18-25 years).

- ContractPeriodCategory: Categorized contract periods into "1 month," "1-6 months," and "6-12 months."

- AdditionalChargesCategory: Classified members as Low, Medium, or High Spenders based on additional charges.

- ClassFrequencyCategory: Segmented class attendance into Low, Medium, and High Frequency.

- LifetimeCategory: Categorized membership lifetimes.

- LocationCategory: Grouped members as "Lives Near Gym" or "Lives Far from Gym."

### DAX Calculations

I utilized DAX to create measures and calculated columns:

1. #### Measures:

- Total Members: COUNTROWS(gym_churn)

- Active Members: CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "No")

- Churned Members: CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "Yes")

- Churn Rate: gym_churn[Churned Members] / gym_churn[Total Members]

- Avg. Additional Charges: AVERAGE(gym_churn[Avg_additional_charges_total])

2. #### Calculated Columns:

- AdditionalChargesCategory: Categorized spending as Low, Medium, or High Spenders.

- AgeCategory: Grouped members into age brackets.

- ChurnRiskCategory: Segmented members into High, Medium, and Low Risk based on contract period, location, and attendance.

- ClassFrequencyCategory: Segmented attendance frequency into Low, Medium, and High.

- ContractPeriodCategory: Grouped contract periods into ranges.

- LifetimeCategory: Categorized membership duration.

- LocationCategory: Classified members by proximity to the gym.

## Visualization

The dashboard includes:

1. KPIs: Displaying Total Members, Active Members, Churned Members, Churn Rate, and Avg. Additional Charges.

2. Pie Chart: Visualizing churn by gender.

3. Bar Charts:

- Churn by Contract Period.

- Churn by Lifetime.

- Churn by Age.

- Churn by Class Frequency.

- Churn by Additional Charges.

4. Filters: Gender and Location filters for interactive analysis.

## Key Insights

![image](https://github.com/user-attachments/assets/08726a6b-929e-4875-8ef3-b4ffe5ad93f1)

#### 1. Churn by Gender:
   
- Male Churn Rate: Approximately 51% of churned members are male.

- Female Churn Rate: The remaining 49% are female.

- The churn rate is fairly balanced between genders, suggesting churn mitigation strategies should target both genders equally.

![image](https://github.com/user-attachments/assets/1ddcc8e0-421b-4ded-a581-417adde38150)

#### 2. Churn by Age:
   
- 18-25 Years: Highest churn rate at 66%.
   
- 36-41 Years: Lowest churn rate at 9%.

- Younger members (18-30 years) are at a much higher risk of leaving the gym. Tailored engagement programs, such as fitness challenges and social events, can help retain this demographic.

![image](https://github.com/user-attachments/assets/352f6336-b982-4fa3-b8fb-096e48ecc6e4)

#### 3. Churn by Contract Period:

- 1-Month Contracts: The highest churn rate at 42%.

- 1-6 Month Contracts: Moderate churn rate at 12%.

- 6-12 Month Contracts: Lowest churn rate at 2%.

- Members on shorter contracts are more likely to churn. Incentivizing longer-term contracts with discounts or added benefits could significantly reduce churn.

![image](https://github.com/user-attachments/assets/8fdfc1c0-da90-4279-b09e-83a19b60eed6)

#### 4. Churn by Lifetime:

- Less than 3 Months: Highest churn rate at 42%.

- 3-6 Months: Churn rate decreases to 4%.

- 6-12 Months: Churn is negligible for members beyond 6 months.

- Members are most vulnerable to churn within the first three months. Strengthening onboarding programs and offering early engagement incentives are critical during this period.

![image](https://github.com/user-attachments/assets/21a669d3-40bb-489b-a35f-cb3d6a98cd3c)

#### 5. Churn by Class Frequency

- Low Frequency (≤1 visit/month): Churn rate at 35%.

- Medium Frequency (1-2 visits/month): Churn rate at 37%.

- High Frequency (>2 visits/month): Lowest churn rate at 14%.

- Members with higher class attendance are more engaged and less likely to churn. Encouraging consistent gym visits through rewards or personalized plans could boost retention.

![image](https://github.com/user-attachments/assets/e85b43a0-54e4-4a6b-8da4-1d6528ad8fa7)

#### 6. Churn by Additional Charges

- Low Spenders (<$50): Highest churn rate at 36%.

- Medium Spenders ($50-$150): Churn rate at 32%.

- High Spenders (>$150): Lowest churn rate at 18%.

- Members who spend more on additional services, such as personal training or nutrition counseling, are less likely to leave. Promoting these services through bundled packages or trials can increase engagement.

## Dashboard

![image](https://github.com/user-attachments/assets/02863b61-f392-41d6-853e-32074dae3836)

## Recommendations

1. Promote Long-Term Contracts:

- Offer discounts or loyalty rewards for 6-12 month memberships.

2. Engage New Members:

- Focus on onboarding programs and personalized fitness plans during the first three months.

3. Target Younger Members:

- Implement youth-oriented campaigns and social activities to retain members aged 18-25.

4. Encourage Class Participation:

- Introduce rewards for frequent class attendance to boost engagement.

5. Upsell Additional Services:

- Promote personal training and premium services to reduce churn among low spenders.

6. Segment and Target:

- Use churn risk categories to develop retention strategies for high-risk members.

