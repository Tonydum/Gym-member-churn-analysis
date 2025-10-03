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
This project analyzes gym membership churn to identify patterns, predict attrition risk, and recommend retention strategies. Churn is a critical metric for subscription-based businesses, as reducing attrition directly improves customer lifetime value and profitability.  

---

## 📊 Dataset  
- **Source**: Public gym membership dataset (single flat file).  
- **Rows**: X records | **Columns**: Y features  
- **Features include**:  
  - Demographics: Age, Gender, Location  
  - Membership details: Contract type, Tenure, Monthly charges  
  - Engagement: Class attendance, PT sessions, facility visits  
  - Target variable: Churn (Yes/No)  

---

## 🛠️ Tools & Skills Used  
- **Power BI**: Data cleaning, DAX measures, and dashboard creation  
- **Excel**: Initial exploration  
- **Python (optional)**: Exploratory analysis or churn prediction  

---

## 📈 KPIs & Measures  
Since this was a flat table, KPIs were derived using calculated columns and measures in Power BI:  
- **Churn Rate** = (# Churned ÷ Total Members)  
- **Retention Rate** = 1 – Churn Rate  
- **Average Tenure** = AVERAGE(Tenure)  
- **Revenue at Risk** = SUM(Monthly Charges for churned members)  
- **Churn by Segment** = breakdowns by contract type, age group, gender, and activity levels  

```DAX
Churn Rate = 
DIVIDE(
    CALCULATE(COUNTROWS('Members'), 'Members'[Churn] = "Yes"),
    COUNTROWS('Members')
)


6. Segment and Target:

- Use churn risk categories to develop retention strategies for high-risk members.

