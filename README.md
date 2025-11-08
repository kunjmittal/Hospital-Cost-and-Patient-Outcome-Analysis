# 🏥 Hospital Cost & Patient Outcome Analysis

### 📌 Overview
This project analyzes hospital treatment costs, readmission rates, and patient outcomes across departments using **SQL and Excel**.  
The goal is to uncover key cost drivers and measure outcome-based efficiency through data-driven insights.

---

### 🎯 Objectives
- Identify cost patterns across departments and diagnoses.  
- Measure KPIs such as **average treatment cost, length of stay, and readmission rate**.  
- Highlight inefficiencies and recommend potential cost-saving opportunities.  
- Create an interactive Excel dashboard for non-technical hospital administrators.

---

### 🧰 Tools & Technologies
- **SQL** – Data cleaning, transformation, KPI computation.  
- **Excel** – Visualization, slicers, pivot tables, KPI dashboard.

---

### 🗂️ Dataset
Simulated hospital dataset containing ~10,000 patient records with:
- Patient ID, Age, Gender  
- Department, Diagnosis, Procedure Cost  
- Length of Stay, Readmission Flag, Outcome

---

### ⚙️ Key SQL Steps
```sql
-- Calculate average cost and length of stay by department
SELECT department,
       ROUND(AVG(treatment_cost),2) AS avg_cost,
       ROUND(AVG(length_of_stay),1) AS avg_stay,
       SUM(CASE WHEN readmission_flag='Yes' THEN 1 ELSE 0 END)*100.0/COUNT(*) AS readmission_rate
FROM hospital_data
GROUP BY department
ORDER BY avg_cost DESC;
