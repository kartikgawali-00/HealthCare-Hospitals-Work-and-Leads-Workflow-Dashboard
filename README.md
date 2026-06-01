# 🏥 HealthCare Hospitals : Work and Leads Workflow Dashboard

<p align="center">
  <img src="https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black">
  <img src="https://img.shields.io/badge/SQL-Data%20Analysis-blue">
  <img src="https://img.shields.io/badge/Excel-Data%20Preparation-green">
  <img src="https://img.shields.io/badge/Project-Interactive%20Dashboard-orange">
</p>

---

# 📌 Project Overview

The **HealthCare Hospitals Work and Leads Workflow Dashboard** is an end-to-end Business Intelligence project developed using **Power BI, SQL, and Excel** to analyze hospital patient workflows, billing patterns, bed occupancy, diagnosis trends, and doctor performance.

The dashboard transforms raw hospital data into meaningful business insights, helping healthcare administrators understand patient flow, optimize resource allocation, monitor billing vs insurance coverage, and improve overall operational efficiency.

---

# 📂 Dataset Used

📊 **Dataset Link**

<a href="https://github.com/kartikgawali-00/HealthCare-Hospitals-Work-and-Leads-Workflow-Dashboard/blob/main/Papollo-Healtcare-Dataset.xlsx">View Dataset</a>

---

# 🎯 Project Objective

The objective of this project is to analyze hospital data and provide actionable insights into:

✅ Patient Admission & Discharge Trends

✅ Billing & Health Insurance Analysis

✅ Bed Occupancy Patterns

✅ Diagnosis Type Distribution

✅ Doctor Performance & Feedback Volume

✅ Follow-Up Scheduling

✅ Revenue vs Insurance Coverage Gap

✅ Ward-Wise Resource Utilization

The dashboard enables data-driven decision-making and supports hospital management through operational optimization.

---

# 🛠️ Tools & Technologies Used

| Technology     | Purpose                     |
| -------------- | --------------------------- |
| 📊 Power BI    | Dashboard Development       |
| 🗄️ SQL        | Data Analysis               |
| 📑 Excel       | Data Cleaning & Preparation |
| ⚡ DAX          | KPI & Measure Creation      |
| 🔄 Power Query | Data Transformation         |

---

# 📂 Dataset Information

The dataset contains hospital patient and operational information including:

* Patient ID
* Admit Date
* Discharge Date
* Follow-Up Date
* Billing Amount
* Health Insurance Amount
* Bed Type (Private / General / ICU)
* Diagnosis Type
* Doctor Name
* Feedback Volume

---

# 📊 Dashboard Overview

## 1️⃣ Key KPIs

| KPI                    | Value         |
| ---------------------- | ------------- |
| 📅 Admit Date          | 12/5/2022     |
| 🏥 Discharge Date      | 12-01-2023    |
| 📋 Follow Up Date      | 15-01-2023    |
| 💰 Billing Amount      | ₹190M         |

---

## 2️⃣ Bed Occupancy Analysis

### ❓ Business Questions

* Which ward type has the highest patient occupancy?
* How are beds distributed across Private, General, and ICU wards?
* Are ICU beds being optimally utilized?

### 💡 Key Insights

✅ Private ward records the highest bed occupancy (~3.5K).

✅ General ward follows with moderate occupancy (~2.5K).

✅ ICU occupancy is the lowest (~1K), indicating specialized care demand.

✅ Resource reallocation from General to ICU may be needed during peak periods.

---

## 3️⃣ Doctor Feedback & Volume Analysis

### ❓ Business Questions

* Which doctors handle the highest patient volume?
* Is feedback volume evenly distributed across doctors?
* Which doctors may need additional support or staffing?

### 💡 Key Insights

✅ All top doctors (Jay Sinha, Jaya Yaadav, Mark Joy, Niki Sharma, Naresh G., Ravi D., Tejas Saxena) each handle approximately **1.02K** feedback cases.

✅ Workload appears evenly distributed, suggesting a balanced staffing model.

✅ No single doctor is significantly overloaded compared to peers.

---

## 4️⃣ Diagnosis Type Analysis

### ❓ Business Questions

* Which diagnosis types are most prevalent?
* How does patient volume vary by disease category?
* Which conditions drive the highest hospital load?

### 💡 Key Insights

✅ **Viral Infection** is the most common diagnosis (highest volume).

✅ **Flu** is the second most frequent diagnosis.

✅ **Malaria** accounts for **1.43K** cases; **Typhoid** for **1.15K** cases.

✅ **Pneumonia** (0.57K) and **Fracture** (0.29K) are less frequent but high-cost conditions.

✅ Infectious diseases dominate, suggesting a need for preventive care programs.

---

## 5️⃣ Billing Amount VS Health Insurance Amount Analysis

### ❓ Business Questions

* How does billing amount compare to health insurance coverage across diagnoses?
* Which conditions have the largest insurance gap?
* Where are patients most financially exposed?

### 💡 Key Insights

✅ **Viral Infection** generates the highest billing (₹53M) with ₹48M insurance coverage — a ₹5M gap.

✅ **Flu** billing is ₹46M against ₹41M insurance coverage.

✅ **Malaria** billing stands at ₹38M with ₹34M covered by insurance.

✅ **Typhoid** shows ₹30M billing vs ₹27M insurance — consistent gap pattern.

✅ **Pneumonia** and **Fracture** have the smallest billing amounts (₹15M and ₹8M) with corresponding insurance values of ₹14M and ₹7M.

✅ Across all diagnoses, **billing consistently exceeds insurance coverage**, highlighting a systemic patient out-of-pocket expense issue.

### 📷 Dashboard Preview

<img src="https://github.com/kartikgawali-00/HealthCare-Hospitals-Work-and-Leads-Workflow-Dashboard/blob/main/Dashboard%20Image/Screenshot%202026-06-01%20182716.png?raw=true">

---

# 🔍 SQL Analysis

### Total Billing Amount

```sql
SELECT SUM(Billing_Amount) AS Total_Billing
FROM Hospital_Data;
```

### Billing vs Insurance by Diagnosis

```sql
SELECT Diagnosis_Type,
       SUM(Billing_Amount) AS Total_Billing,
       SUM(Health_Insurance_Amount) AS Total_Insurance,
       SUM(Billing_Amount) - SUM(Health_Insurance_Amount) AS Insurance_Gap
FROM Hospital_Data
GROUP BY Diagnosis_Type
ORDER BY Total_Billing DESC;
```

### Bed Occupancy by Ward Type

```sql
SELECT Bed_Type,
       COUNT(*) AS Total_Occupancy
FROM Hospital_Data
GROUP BY Bed_Type
ORDER BY Total_Occupancy DESC;
```

### Doctor Feedback Volume

```sql
SELECT Doctor_Name,
       COUNT(*) AS Feedback_Count
FROM Hospital_Data
GROUP BY Doctor_Name
ORDER BY Feedback_Count DESC;
```

### Patient Admission Trend

```sql
SELECT CAST(Admit_Date AS DATE) AS Admit_Day,
       COUNT(*) AS Total_Admissions
FROM Hospital_Data
GROUP BY CAST(Admit_Date AS DATE)
ORDER BY Admit_Day;
```

---

# 📈 DAX Measures

### Total Billing Amount

```DAX
Total Billing =
SUM(Hospital[Billing_Amount])
```

### Total Insurance Amount

```DAX
Total Insurance =
SUM(Hospital[Health_Insurance_Amount])
```

### Insurance Coverage Gap

```DAX
Insurance Gap =
[Total Billing] - [Total Insurance]
```

### Total Patients

```DAX
Total Patients =
COUNTROWS(Hospital)
```

### Average Billing Per Patient

```DAX
Avg Billing Per Patient =
DIVIDE(
    [Total Billing],
    [Total Patients]
)
```

---

# 💡 Project Insights

## 🏥 Patient & Operational Insights

* Private ward has the highest occupancy, indicating patient preference for private care.
* ICU demand is lower but represents high-cost, critical cases.
* Workload is well-balanced across the medical team.

## 💰 Billing & Insurance Insights

* Total billing amount reached **₹190 Million**.
* Insurance coverage consistently falls short of billing across all diagnosis types.
* Viral Infection and Flu are the highest revenue-generating conditions.

## 🩺 Diagnosis Insights

* Infectious diseases (Viral Infection, Flu, Malaria, Typhoid) dominate the case load.
* Fractures and Pneumonia are low-volume but require specialized treatment resources.

## 👨‍⚕️ Doctor Performance Insights

* All key doctors maintain similar patient feedback volumes (~1.02K each).
* Equitable distribution suggests effective hospital scheduling practices.

---

# 🚀 Business Recommendations

### 🛏️ Optimize Bed Allocation

Increase ICU capacity during infectious disease outbreaks to handle critical cases efficiently.

### 💳 Improve Insurance Coverage Awareness

Educate patients on insurance claim processes to reduce out-of-pocket expenses across all diagnosis categories.

### 📈 Preventive Care Programs

Launch targeted preventive care campaigns for Viral Infection and Flu to reduce high-volume admission loads.

### 👨‍⚕️ Doctor Workload Monitoring

Monitor doctor feedback volume regularly to identify early signs of burnout or overload.

### 📋 Follow-Up Process Optimization

Streamline the follow-up scheduling process to reduce gaps between discharge and follow-up dates.

---

# 🏆 Skills Demonstrated

### 📊 Power BI

* Interactive Dashboard Development
* Data Modeling
* DAX Measures
* Power Query
* Drill-Down Analysis
* Donut Chart & Bar Chart Visualization
* Line Chart for Trend Analysis
* KPI Card Design
* Slicer & Filter Configuration

### 🗄️ SQL

* Aggregations
* Group By
* Date Functions
* Billing & Insurance Gap Analysis
* Diagnosis-Wise Revenue Analysis

### 📑 Excel

* Data Cleaning
* Data Validation
* Data Preparation

---

# 📌 Final Conclusion

The HealthCare Hospitals Work and Leads Workflow Dashboard provides a comprehensive view of patient admissions, bed occupancy, billing performance, insurance coverage gaps, diagnosis distributions, and doctor workload.

The analysis reveals strong demand for infectious disease treatment, consistent billing-to-insurance gaps across all conditions, and balanced doctor workloads. These insights can help hospital management optimize bed allocation, improve billing processes, and design targeted preventive health programs to reduce patient load and improve care outcomes.

---

# 👨‍💻 Author

## Kartik Gawali

📊 Data Analyst | Power BI | SQL | Excel

⭐ If you found this project useful, don't forget to star the repository.
