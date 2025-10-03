# 🏋️ Gym Member Churn Analysis  

## 📑 Table of Contents
1. [Project Overview](#-project-overview)  
2. [Dataset](#-dataset)  
3. [Tools & Skills Used](#-tools--skills-used)  
4. [KPIs & Measures](#-kpis--measures)  
5. [Dashboard Highlights](#-dashboard-highlights)  
6. [Business Impact](#-business-impact)  
7. [How to Use](#-how-to-use)  
8. [Next Steps](#-next-steps)  

---

## 📌 Project Overview  
This project analyzes gym membership churn to identify patterns, predict attrition risk, and recommend retention strategies. 
Churn is a critical metric for subscription-based businesses, as reducing attrition directly improves customer lifetime value and profitability.  

---

## 📊 Dataset  
- **Source**: Public gym membership dataset (single flat file).  
- **Rows**: 4000 records | **Columns**: 14 features  
- **Features include**:  
  - Demographics: Age, Gender, Location  
  - Membership details: Contract type, Tenure, Monthly charges  
  - Engagement: Class attendance, PT sessions, facility visits  
  - Target variable: Churn (Yes/No)  

---

## 🛠️ Tools & Skills Used  
- **Power BI**: Data cleaning, DAX measures, and dashboard creation  
- **Excel**: Initial exploration  

---

## 📈 KPIs & Measures  
Since this was a flat table, KPIs were derived using calculated columns and measures in Power BI:  
- **Churn Rate** = (# Churned ÷ Total Members)  
- **Retention Rate** = 1 – Churn Rate  
- **Average additional Charges** = AVERAGE(Additional charges)  
- **Churn by Segment** = breakdowns by contract type, age group, gender, and activity levels  

```DAX
Total Members = COUNTROWS(gym_churn)
Churned Members = CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "Yes")
Active Members = CALCULATE(gym_churn[Total Members], gym_churn[Churn_label] = "No")
Churn Rate = DIVIDE(gym_churn[Churned Members], gym_churn[Total Members])

AgeCategory = 
SWITCH(
    TRUE(),
    gym_churn[Age] < 25 && gym_churn[Age] <= 25, "18-25 years",
    gym_churn[Age] < 26 && gym_churn[Age] <= 30, "26-30 years",
    gym_churn[Age] < 31 && gym_churn[Age] <= 35, "31-35 years",
    "36-41 years"
)

ContractPeriodCategory = 
SWITCH(
    TRUE(),
    gym_churn[Contract_period] = 1, "1 month",
    gym_churn[Contract_period] <= 6, "1-6 months",
    "6-12 months"
)

AdditionalChargesCategory = 
SWITCH(
    TRUE(),
    [Avg_additional_charges_total] < 50, "Low Spender",
    [Avg_additional_charges_total] >= 50 && [Avg_additional_charges_total] < 150, "Medium Spender",
    [Avg_additional_charges_total] >= 150, "High Spender",
    "Unknown"
)
```


## 📊 Dashboard Highlights
Key visuals from the Power BI dashboard:

Churn by Contract Type → Month-to-month contracts had the highest churn.

Demographic Insights → Younger members churn faster than older, long-tenure members.

Engagement Impact → Members attending more classes had significantly lower churn rates.


Screenshots


![image](https://github.com/user-attachments/assets/352f6336-b982-4fa3-b8fb-096e48ecc6e4)


![image](https://github.com/user-attachments/assets/e85b43a0-54e4-4a6b-8da4-1d6528ad8fa7)


![image](https://github.com/user-attachments/assets/8fdfc1c0-da90-4279-b09e-83a19b60eed6)


![image](https://github.com/user-attachments/assets/02863b61-f392-41d6-853e-32074dae3836)



## 💡 Business Impact
Identified high-risk customer segments for targeted retention campaigns.

Demonstrated the link between engagement and loyalty, helping managers focus on increasing class attendance.

Quantified the financial cost of churn, supporting data-driven decisions for retention budgeting.

Suggested initiatives like contract incentives and loyalty rewards to improve retention.


## 🚀 How to Use

Clone or download the repository.

Open the Gym-Churn-Analysis.pbix file in Power BI Desktop.

No data connection required — the dataset (CSV) is included and already loaded.


## 📌 Next Steps

Add a predictive churn probability model (Python + Power BI integration).

Automate churn reporting with scheduled refresh in Power BI Service.

Extend analysis to simulate retention campaign scenarios.
