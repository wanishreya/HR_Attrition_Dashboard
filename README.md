# HR Employee Attrition Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-FFB90F?style=for-the-badge)

## 📊 Project Overview

This Power BI dashboard analyzes employee attrition factors using a dataset of 1,470 employees from IBM. The dashboard provides actionable insights to help HR teams understand why employees leave and implement data-driven retention strategies.

**Dataset:** IBM HR Analytics Employee Attrition Dataset  
**Tools Used:** Microsoft Excel, Power BI, DAX  
**Time Period:** 1,470 employee records with 35+ attributes

---

## 🎯 Key Insights

| Insight | Finding | Business Impact |
|---------|---------|-----------------|
| **Overall Attrition** | 16.1% (237 employees) | Above industry average - needs attention |
| **Overtime Impact** | 30% attrition for overtime vs 10% for non-overtime | 3x higher risk - address workload/burnout |
| **Age Factor** | 25-34 age group accounts for 38% of all attrition | Career development needed for early-career staff |
| **Promotion Gap** | No promotion in 5+ years = 2x higher attrition risk | Career pathing essential |
| **Satisfaction Link** | Low satisfaction employees: 22.6% attrition vs 10.2% for high satisfaction | Engagement programs critical |
| **Department Analysis** | Sales department shows highest attrition rate (18.2%) | Review sales targets and compensation |

---

## 📁 Files Included

| File Name | Description |
|-----------|-------------|
| `HR_Attrition_Dashboard.pbix` | Main Power BI dashboard file with all visualizations and DAX measures |
| `data/HR_Attrition_Cleaned.xlsx` | Cleaned dataset with calculated columns (Age Group, Income Band, Tenure Group) |
| `screenshots/` | Folder containing preview images of all dashboard pages |

---

## 📋 Dashboard Pages

### Page 1: Executive Summary
- Key KPIs: Total Employees (1,470), Attrition Count (237), Attrition Rate (16.1%)
- High-level overview of attrition by department, gender, and age group
- Interactive slicers for filtering by department, gender, age group, and job role

### Page 2: Department & Job Analysis
- Detailed breakdown of attrition by department and job role
- Comparison of attrition rates across Research & Development, Sales, and HR
- Job role-wise attrition analysis with employee counts

### Page 3: Satisfaction & Work-Life Analysis
- Attrition patterns by job satisfaction levels (1-4)
- Impact of work-life balance on employee retention
- Comparison of key drivers: overtime, low satisfaction, poor work-life balance

### Page 4: Demographics & Tenure Analysis
- Attrition analysis by marital status, education field, and income band
- Tenure-based attrition patterns (0-2 years, 3-5 years, 6-10 years, 10+ years)
- High-risk segment identification

---

## 🛠️ Key DAX Measures Created

```DAX
// Core KPIs
Total Employees = COUNTROWS(Sheet1)
Attrition Count = CALCULATE(COUNTROWS(Sheet1), Sheet1[Attrition] = "Yes")
Attrition Rate = DIVIDE([Attrition Count], [Total Employees], 0)

// Key Insights
Overtime Attrition Rate = 
DIVIDE(
    CALCULATE([Attrition Count], Sheet1[OverTime] = "Yes"),
    CALCULATE([Total Employees], Sheet1[OverTime] = "Yes"),
    0
)

No Promotion Attrition Rate = 
DIVIDE(
    CALCULATE([Attrition Count], Sheet1[YearsSinceLastPromotion] >= 5),
    CALCULATE([Total Employees], Sheet1[YearsSinceLastPromotion] >= 5),
    0
)

Age25-34 Attrition Rate = 
DIVIDE(
    CALCULATE([Attrition Count], Sheet1[Age Group] = "25-34"),
    CALCULATE([Total Employees], Sheet1[Age Group] = "25-34"),
    0
)
