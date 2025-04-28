# 📚 Crime Data Analytics Project

## 📌 Project Name
# Crime Incidents Analysis: Trends, Patterns, and Insights (2020–Present)

---

## 📖 Project Overview
This project focuses on analyzing crime incidents reported from 2020 to the present in Los Angeles. The goal is to uncover patterns, trends, and actionable insights that can support public safety initiatives, inform policy-making, and guide community awareness efforts.

---


## 🎯 Objective
- Analyze the types, locations, and frequency of crimes.
- Identify temporal and geographical crime trends.
- Understand victim demographics and common crime weapons.
- Provide insights to assist decision-making by public authorities, researchers, and citizens.
- Assess the possibility of predictive modeling to forecast crime occurrence patterns.

---

## 🗂️ Data Source
- **Dataset:** [Crime Data from 2020 to Present](https://catalog.data.gov/dataset/crime-data-from-2020-to-present)

---

## 🛠️ Tools & Techniques Used
- **Python (Pandas, NumPy, Matplotlib, Seaborn)**
- **Jupyter Notebook**
- **Tableau / Power BI** for dashboard visualization
- **Data Cleaning Techniques** (Handling missing values, removing duplicates, removing outliers)
- **Exploratory Data Analysis (EDA)**
- **Optional Predictive Modeling** (if suitable)

---

## 🧹 Data Cleaning & Preparation
- Dropped irrelevant columns (`Crm Cd 2`, `Crm Cd 3`, `Crm Cd 4`).
- Removed missing values.
- Removed duplicate entries.
- Replaced inconsistent values (`X`, `H` in `Vict Sex` column) with random gender values (`M` or `F`).
- Detected and removed numerical outliers based on the IQR method.
- Converted appropriate columns (e.g., `DATE OCC`, `Date Rptd`) into proper datetime types.

---

## 📊 Exploratory Data Analysis (EDA) Questions

1. **What are the top 10 most frequent crime types reported?**
2. **Which areas (districts) have the highest crime rates?**
3. **What are the peak months and times when most crimes occur?**
4. **How does victim age and gender distribution vary across different crime types?**
5. **Which weapons are most commonly used in reported crimes?**

---


## 📈 Suitability for Modeling and Decision-Making

- ✅ **Decision-Making:**  
  The dataset is highly suitable for descriptive analytics and decision support:
  - Trend identification (monthly/yearly crime spikes)
  - Resource allocation for law enforcement based on high-crime areas
  - Public awareness campaigns focused on vulnerable demographics
 

- ⚡ **Predictive Modeling:**  
  Modeling can be considered, but with limitations:
  - Predicting the type of crime based on time, location, victim demographics, and previous patterns is possible.
  - However, careful feature engineering would be needed because some fields (e.g., MO Codes, Cross Streets) may require encoding or deeper domain understanding to use effectively.

  Possible models:
  - **Classification Models:** Predict crime category based on features.
  - **Clustering Models:** Segment crime incidents into patterns or clusters.


