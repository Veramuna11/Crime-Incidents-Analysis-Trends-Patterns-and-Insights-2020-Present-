# 📚 Crime Data Analytics Project

## 📌 Project Name
# Crime Incidents Analysis: Trends, Patterns, and Insights (2020–Present)

---


## 📑 Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Data Source](#data-source)
- [Tools & Techniques Used](#tools--techniques-used)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Top 10 Crime Types](#top-10-crime-types)
  - [Top Areas with Highest Crime Rates](#top-areas-with-highest-crime-rates)
  - [Peak Months and Times when Most Crimes Occur](#peak-months-and-times-when-most-crimes-occur)
  - [Victim Age Distribution](#victim-age-distribution)
  - [Victim Gender Distribution](#victim-gender-distribution)
  - [Most Commonly Used Weapons](#most-commonly-used-weapons)
- [Key Findings](#key-findings)
- [Decision-Making Insights](#decision-making-insights)
- [Tableau Dashboard](#tableau-dashboard)
- [Conclusion](#conclusion)
- [Recommendations](#recommendations)
- [Future Work and Next Steps](#future-work-and-next-steps)


---

## 📖 Project Overview
This project focuses on analyzing crime incidents reported from 2020 to the present in Los Angeles. The goal is to uncover patterns, trends, and actionable insights that can support public safety initiatives, inform policy-making, and guide community awareness efforts.

---


## 🎯 Objectives
- Analyze the types, frequency, and location of reported crimes.
- Identify crime hotspots and seasonal crime trends.
- Understand victim demographics across different crime types.
- Provide insights to assist decision-making by public authorities and researchers.

  
---


  ## 🗂️ Data Source
- [Crime Data from 2020 to Present - Data.gov](https://catalog.data.gov/dataset/crime-data-from-2020-to-present)

---


---

## 🛠️ Tools & Techniques Used
- **Python**: Pandas, NumPy, Matplotlib, Seaborn
- **Jupyter Notebook**
- **Data Cleaning Techniques**: Handling missing values, removing duplicates, outlier detection
- **Exploratory Data Analysis (EDA)**
- **Visualization**: Bar plots, histograms, line plots
- **Decision-Making Recommendations**

> While time series forecasting models (such as ARIMA and Prophet) were considered for predicting future crime rates, the current project scope focused on descriptive analytics to deliver immediate, actionable insights for public safety decision-making. Future extensions could include predictive modeling based on aggregated monthly crime trends.

---


## 🧹 Data Cleaning & Preparation
- Dropped irrelevant columns (`Crm Cd 2`, `Crm Cd 3`, `Crm Cd 4`).
- Removed missing values.
- Removed duplicate entries.
- Replaced inconsistent values (`X`, `H` in `Vict Sex` column) with random gender values (`M` or `F`).
- Detected and removed numerical outliers based on the IQR method.
- Converted appropriate columns (e.g., `DATE OCC`, `Date Rptd`) into proper datetime types.

---

## 📊 Exploratory Data Analysis (EDA)

- **Identified Top 10 Most Frequent Crime Types**
  

![top_10_crimes](https://github.com/user-attachments/assets/65ac5124-6597-4434-98db-4597fe4c747e)


 * Assault with a deadly weapon and aggravated assault are the most reported crimes.
 * Robbery and simple assault also have high incident counts.
 * A significant proportion of crimes involve physical confrontations rather than property crimes.
 * Targeted policing efforts should focus on preventing violent crimes, particularly aggravated assaults and robberies.

---

- **Analyzed Top Areas with Highest Crime Rates**
  
![top_areas_crime](https://github.com/user-attachments/assets/a7afc399-99ca-40be-bc5e-0ea75b149728)


* 77th Street, Southeast, and Southwest districts reported the highest number of crime incidents.
* These areas are consistent hotspots for criminal activities.
* Focused policing strategies, community programs, and resource deployments should prioritize these top three districts to achieve maximum impact on crime reduction.


---

  
- **Examined Peak Months and Times for Crimes**
  
![crimes_per_month](https://github.com/user-attachments/assets/35ffb384-0c65-48c6-afe3-7a2ae5239cc3)


* Crime incidents were highest in January and February.
* There is a gradual decline from March to May.
* After May, crime rates remain consistently low till December.
* Early months (Jan–Mar) show a seasonal spike, suggesting the need for increased policing and community awareness campaigns during this period. """)


---
  
- **Explored Victim Age and Gender Distributions**

  ![victim_age_distribution](https://github.com/user-attachments/assets/279c492a-82a4-4075-9bc7-78aae754b476)

* The majority of crime victims fall within the 20 to 40-year age range.
* A significant number of victims are also aged between 0 to 10 years, indicating crimes involving minors.
* After 40 years, the number of victims gradually declines.
* Crime prevention efforts and victim support programs should primarily focus on young adults and also address child safety concerns

---

  ![victim_gender_distribution](https://github.com/user-attachments/assets/ceb3cf24-d336-493e-a20f-ff36afe0a668)


* Males tend to be slightly more represented, but females also experience a significant number of incidents.
* Approximately 60% of the victims are male, and 40% are female.
* Crime prevention programs should be inclusive but may consider slightly tailoring interventions toward male-dominated victim demographics.


---

- **Investigated Most Commonly Used Weapons**

![top_weapons_used](https://github.com/user-attachments/assets/212f956d-604c-4f22-ac0e-a3c8cd5f2426)

* The majority of crimes involve the use of bodily force (hands, fists, feet) rather than traditional weapons.
* Handguns are the second most commonly used weapons in reported crimes.
* Unknown or unreported weapons also make up a significant proportion.
* Crime prevention strategies should emphasize awareness on self-defense, conflict de-escalation, and firearm regulation

---

## Data Analysis
**Import neccessay Labraries**

```Python

## Import Libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Display settings
pd.set_option('display.max_columns', None)
```

## **Loading of the Dataset**
```Python

# Load the CSV file
df = pd.read_csv('Crime_Data_from_2020_to_Present.csv')

# Display the first 5 rows to inspect
df.head()
```

**Check for Missing Values**
```Python
missing_values = df.isnull().sum()
print("\nMissing values per column:")
print(missing_values)
```

**Drop Columns**
```Python
# Drop the specified columns
columns_to_drop = ['Crm Cd 2', 'Crm Cd 3', 'Crm Cd 4']
df.drop(columns=columns_to_drop, axis=1, inplace=True)

# Check to confirm
df.head()
```

**Check for missing values**
```Python
# Show missing values
print(df.isnull().sum())

# Remove rows with missing values
df.dropna(inplace=True)

# Confirm no more missing values
print(df.isnull().sum())
```

**Remove Duplicate Rows**
```Python
# Check duplicates
print(f"Duplicate rows before removal: {df.duplicated().sum()}")

# Remove duplicates
df.drop_duplicates(inplace=True)

# Confirm
print(f"Duplicate rows after removal: {df.duplicated().sum()}")
```

**Remove Outliers (Numerical Columns Only)**
``` Phyton

# Select numeric columns
numeric_cols = df.select_dtypes(include=np.number).columns

# Remove outliers for each numeric column
for col in numeric_cols:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    df = df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]

# Confirm after outlier removal
df.shape
```

**Convert Data Types**
```Python
# Check data types
print(df.dtypes)

# If there is a column like 'DATE OCC', convert it to datetime
if 'DATE OCC' in df.columns:
    df['DATE OCC'] = pd.to_datetime(df['DATE OCC'], errors='coerce')

# Confirm
print(df.dtypes)
```

**Convert Data Types**
```Python

import random

# Define a function to replace 'X' or 'H' randomly with 'M' or 'F'
def replace_with_random(value):
    if value in ['X', 'H']:
        return random.choice(['M', 'F'])
    else:
        return value

# Apply the function to Vict Sex column
df['Vict Sex'] = df['Vict Sex'].apply(replace_with_random)

# Check the unique values to confirm
print(df['Vict Sex'].unique())
```

## 🧠 Key Findings
- Crime incidents peak during the early months of the year (January to March).
- Assaults and robberies dominate reported crimes.
- 77th Street, Southeast, and Southwest areas experience the highest crime rates.
- Victims are predominantly young adults aged 20–40 years.
- Most crimes involve bodily force, with handguns being the most common weapon among armed incidents.

---

## 📊 Tableau Dashboard 

To further enhance interactivity, a Tableau dashboard was developed featuring:

- KPI Overview
- Top 10 Crime Types
- Top Crime Areas
- Crime Trends Over Time
- Victim Age and Gender Distribution
- Most Common Weapons Used

▶️ **[View Interactive Tableau Dashboard Here](your-tableau-public-link-here)**

---

## 🧠 Conclusion

The analysis of Los Angeles crime data from 2020 to the present revealed distinct patterns and actionable insights. Crime incidents concentrate heavily at the start of the year, with assaults and robberies topping crime reports, especially in 77th Street and Southeast areas. Victims are largely young adults, and physical altercations are more common than armed confrontations. These findings guide targeted safety initiatives, strategic resource allocation, and public education campaigns.

---


## 📖 Decision-Making Insights
- Increase law enforcement deployment and community engagement between January and March to address seasonal crime spikes.
- Prioritize hotspot areas (77th Street, Southeast, Southwest) for policing and intervention programs.
- Launch public safety campaigns targeting young adults and child protection efforts.
- Promote conflict de-escalation training and self-defense awareness initiatives.
- Improve weapon reporting practices to enhance future crime analysis accuracy.

---

## 📋 Future Work and Next Steps

- Expand feature set with socio-economic, demographic, and neighborhood-level data.
- Address class imbalance using oversampling or undersampling methods for future modeling.
- Apply unsupervised learning models such as clustering (e.g., KMeans) to detect hidden crime patterns.
- Develop time series forecasting models (e.g., ARIMA, Prophet) on aggregated monthly crime counts for proactive resource planning.
- Create dynamic crime heatmaps using geographic coordinates to identify micro-level hotspots.
- Analyze the impact of societal changes (e.g., COVID-19, public protests) on crime dynamics over time.

---

## 👤 Author

Developed by **Ibemere Munachi Vera**, a passionate Data Analyst skilled in Python, SQL, Tableau, and Business Intelligence.  
Dedicated to transforming data into actionable insights that drive smarter decision-making.

- **LinkedIn**: Vera Ibemere
- **GitHub**: [Your GitHub Profile Link]
- **Portfolio**: [Optional Portfolio Website Link]

Feel free to connect for collaborations or exciting data projects!

---
