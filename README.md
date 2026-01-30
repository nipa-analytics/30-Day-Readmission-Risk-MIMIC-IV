# 30-Day-Readmission-Risk-MIMIC-IV
Predicting 30-day hospital readmissions using MIMIC-IV clinical data with SQL-style feature engineering and machine learning.

**Project Overview**

Hospital readmissions within 30 days are a major driver of healthcare costs, patient outcomes, and regulatory penalties. This project builds a patient-level readmission risk model using the MIMIC-IV Clinical Database (Demo v2.2) to:
Predict whether a patient is likely to be readmitted within 30 days
Identify high-risk patients for proactive care management
Demonstrate an end-to-end healthcare ML pipeline from raw EHR data to actionable insights
Healthcare organizations need to:
Reduce avoidable readmissions
Prioritize limited care-management resources
Identify patients requiring post-discharge follow-up

This project simulates a real-world hospital analytics use case aligned with CMS quality metrics and population health initiatives.

**Dataset**

Source: MIMIC-IV Clinical Database (Demo v2.2)

Core Tables Used:

patients

admissions

diagnoses_icd

icustays

Grain: One row per hospital admission, aggregated to patient-level features

Target Variable

30-Day Readmission Flag

1 → Patient readmitted within 30 days of discharge
0 → No readmission within 30 days

The target is engineered by comparing the discharge date with the next admission date per patient.

**Feature Engineering (SQL-Style Analytics)**
All features are derived using joins, window logic, and aggregations that mirror production SQL workflows.

**Feature	Description**

num_prior_admissions	Historical utilization
length_of_stay	Index admission LOS
avg_length_of_stay	Patient-level LOS trend
num_unique_diagnoses	Clinical complexity
chronic_condition_flag	≥ 3 diagnoses
icu_stay_flag	ICU exposure during admission
total_icu_days	Severity indicator
age_at_admission	Demographic risk factor
Data Preparation
Missing values handled by feature type

Categorical variables encoded safely

Numerical features standardized

Class imbalance reviewed before modeling

Train/Test split performed at patient-safe boundaries

Modeling Approach
Problem Type: Binary Classification

Models Implemented:

Logistic Regression (baseline, interpretable)

Random Forest (nonlinear risk patterns)

Evaluation Metrics:

ROC-AUC

Precision / Recall

Confusion Matrix

Emphasis placed on recall to minimize missed high-risk patients.

Key Insights
Prior utilization and diagnosis burden strongly influence readmission risk

ICU exposure significantly increases short-term readmission probability

A small subset of patients accounts for a disproportionate share of risk

These insights directly support care prioritization and discharge planning.

Care Prioritization Framework
Patients are grouped into actionable tiers:

High Risk: Immediate follow-up & care coordination

Medium Risk: Post-discharge monitoring

Low Risk: Standard discharge pathway

This mirrors real hospital case-management workflows.

Tech Stack
Languages: Python, SQL-style analytics

Libraries:

pandas, numpy

scikit-learn

matplotlib, seaborn

Environment: Jupyter Notebook

📁 Project Structure 📦 30-Day-Readmission-Risk-MIMIC-IV ┣ 📄 READMISSION_RISK_PREDICTION.ipynb ┣ 📄 README.md

Future Enhancements
Incorporate labs & vitals

Time-series modeling (LSTM / survival analysis)

Cost-weighted readmission modeling

Dashboard for clinical stakeholders

Author
Nipa Shah Healthcare Analytics | Data Science | Business Analytics 📍 United States

🔗 LinkedIn: (https://www.linkedin.com/in/nipa-s-486287382/)
