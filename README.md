# 📊 Training Analytics Dashboard (BigQuery & Power BI)

## 📌 Project Overview
An end-to-end data analysis project designed to evaluate training programs, track participant performance, and extract actionable insights using **Google BigQuery (SQL)** and **Microsoft Power BI**.

## 🛠️ Tools & Technologies
* **Data Warehousing & Querying:** Google BigQuery (SQL)
* **Data Visualization & BI:** Microsoft Power BI
* **Data Modeling:** Star Schema & DAX Measures

## 🔍 SQL Data Preparation (BigQuery)
Used BigQuery to clean, transform, and aggregate raw training data before connecting it to Power BI:
```sql
-- Example: Replace this with one of your actual BigQuery queries
SELECT 
    program_name,
    COUNT(trainee_id) AS total_trainees,
    AVG(completion_rate) AS avg_completion
FROM `project.dataset.training_data`
GROUP BY program_name;
```
## 📈 Dashboard Preview
<img width="1067" height="506" alt="image" src="https://github.com/user-attachments/assets/31f4ff87-a03f-4e9d-87de-573ca481e9ac" />


## 💡 Key Insights
* **Insight 1:** Write your first key finding here (e.g., highest performing training track).
* **Insight 2:** Write your second key finding here (e.g., completion rates across regions).

