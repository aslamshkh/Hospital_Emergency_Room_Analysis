# 🏥 Hospital Emergency Room Analysis
Excel • Power Query • Power Pivot • DAX • Data Modelling • Dashboarding

A complete end-to-end Excel analytics project analyzing 9,216 Emergency Room visits to uncover operational bottlenecks, wait-time patterns, demographic trends, and satisfaction scores. Built entirely in Microsoft Excel using Power Query, Data Model, PivotTables, and DAX.

---

## 📌 Dashboard Preview

![Dashboard](Hospital%20Emergency%20Room%20Dashboard.png)

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Business Problem](#business-problem)
- [Objectives](#objectives)
- [Dataset Overview](#dataset-overview)
- [Data Cleaning and Transformation](#data-cleaning-and-transformation)
- [DAX Measures](#dax-measures)
- [Key Insights](#key-insights)
- [Dashboard Features](#dashboard-features)
- [Project Files](#project-files)
- [How to Use](#how-to-use)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)

---

## 📘 Project Overview
Emergency Rooms operate in high-pressure environments where delays directly affect patient care.  
This project transforms a raw CSV dataset into an interactive Excel dashboard to analyze:

- Patient volume  
- Admission decisions  
- Wait-time performance  
- Demographic patterns  
- Referral sources  
- Satisfaction levels  

---

## ❗ Business Problem
Hospital teams need answers to questions such as:

- Why are wait times high?
- Which demographics visit the ER most?
- Are admissions balanced?
- Which departments generate the most referrals?
- Does wait time affect satisfaction?

This project provides clear, data-driven insights into these operational questions.

---

## 🎯 Objectives

- Clean raw ER data using Power Query  
- Build a data model using Power Pivot  
- Create calculated columns and DAX measures  
- Develop interactive KPIs and visualizations  
- Identify insights across demographics, wait times, referrals, and satisfaction  

---

## 📁 Dataset Overview

**Records:** 9,216  
**Columns:** 11  
**Format:** CSV  
**Period:** April 2023 – October 2024  

### Key Columns

- Admission DateTime  
- Gender  
- Age  
- Wait Time  
- Admission Flag  
- Department Referral  
- Satisfaction Score  
- Patient name fields (merged during cleaning)

---

## 🧹 Data Cleaning and Transformation
Performed using Power Query.

### Standardization
- Normalized Gender values  
- Split Date and Time into separate fields  
- Created Age Groups (0–19, 20–29, ..., 70–79)  
- Converted True/False admission flag to text  
- Cleaned “None” values in Referral column  
- Removed duplicate Wait Time column  
- Merged First Name and Last Name columns  

### Additional Transformations
- Created a full Date Table  
- Created WaitTime Category (In Time vs Delayed)  
- Removed unnecessary columns  
- Checked for blank Satisfaction Scores (left untouched for transparency)

---

## 📐 DAX Measures
Used inside Power Pivot to drive KPIs.

```DAX
Total Patients := COUNTROWS(PatientData)

Average Wait Time := AVERAGE(PatientData[Wait Time])

Admission Rate :=
DIVIDE(CALCULATE(COUNTROWS(PatientData), PatientData[Admission Flag] = TRUE),
    [Total Patients])

Average Satisfaction := AVERAGE(PatientData[Satisfaction Score])

InTime Patients := CALCULATE([Total Patients], PatientData[WaitTime Category] = "In Time")

Delayed Patients := CALCULATE([Total Patients], PatientData[WaitTime Category] = "Delayed")
```

---

## 📊 Key Insights

### Patient Volume
- 9,216 visits recorded  
- Daily traffic between 20–45 patients  

### Wait Time
- 38% attended within 30 minutes  
- 62% experienced delays  

### Admission Patterns
- 50.04% admitted  
- 49.96% not admitted  

### Satisfaction
- Average Satisfaction Score = 4.99  

### Demographics
- Gender split: 4,729 Male, 4,487 Female  
- Highest visits from age group 70–79  

### Referral Patterns
Top referring departments:
1. General Practice  
2. Orthopedics  
3. Physiotherapy  

Large number of “None” entries indicate walk-ins or missing data.

---

## 🖥 Dashboard Features
- KPI Cards for:
  - Total Patients  
  - Average Wait Time  
  - Average Satisfaction  
  - Admission Rate
    
- Slicers for:
  - Year  
  - Month  
  - Gender  
  - Age Group  
  - Admission Status  
  - Department
    
- Charts:
  - Age Group Bar Chart  
  - Admission Comparison Chart  
  - Gender Pie Chart  
  - Wait-Time Doughnut Chart  
  - Referral Count Bar Chart  

---

## 📂 Project Files
```
Hospital_Emergency_Room_Analysis/
│
├── Hospital Emergency Room Project.xlsx
├── Hospital Emergency Room Data Raw.csv
├── Hospital Emergency Room Dashboard.png
├── Dashboard Layout.png
├── Conditional Column Creation.png
├── WaitTime Categorisation.png
├── Hospital Logo.png
└── README.md
```

---

## 🧭 How to Use

1. Download the Excel project file.  
2. Open in Excel (2016 or later).  
3. Ensure Power Query and Power Pivot are enabled.  
4. Refresh data connections.  
5. Navigate to the Dashboard sheet.  
6. Use slicers to interact with the visuals.  

---

## ⚠ Limitations

- Missing satisfaction scores in some rows  
- Some wait times exceed 180 minutes (left unchanged for transparency)  
- Dataset lacks clinical severity details  

---

## 🚀 Future Improvements

- Migrate dashboard to Power BI  
- Add trend analysis and forecasting  
- Include patient flow modeling  
- Enhance data quality rules  

