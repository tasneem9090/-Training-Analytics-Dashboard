# 📊 Training Analytics Dashboard (BigQuery & Power BI)

## 📌 Project Overview
An end-to-end data analysis project designed to evaluate training programs, track participant performance, and extract actionable insights using **Google BigQuery (SQL)** and **Microsoft Power BI**.

## 🛠️ Tools & Technologies
* **Data Warehousing & Querying:** Google BigQuery (SQL)
* **Data Visualization & BI:** Microsoft Power BI
* **Data Modeling:** Star Schema & DAX Measures

## 🔍 SQL Data Preparation & Analysis (BigQuery)
Used Google BigQuery to join relational tables (`trainees`, `trainings`, `trainers`, `reports`, and `book_distribution`) and aggregate key metrics for Power BI:

```sql
-- 1. Trainees Count per Training Program
SELECT
  tr.training_name,
  COUNT(t.trainee_id) AS trainee_count
FROM trainings.trainees AS t
JOIN trainings.trainings AS tr
  ON t.training_id = tr.training_id
GROUP BY tr.training_name
ORDER BY trainee_count DESC;

-- 2. Reports Submitted per Trainer
SELECT 
  t.first_name, 
  t.last_name, 
  COUNT(r.report_id) AS report_count 
FROM trainings.reports AS r 
JOIN trainings.trainers AS t 
  ON r.trainer_id = t.trainer_id 
GROUP BY t.first_name, t.last_name 
ORDER BY report_count DESC;

-- 3. Demographics Breakdown (Gender & Nationality)
SELECT 
  gender, 
  nationality, 
  COUNT(trainee_id) AS trainee_count 
FROM trainings.trainees 
GROUP BY gender, nationality 
ORDER BY trainee_count DESC;

-- 4. Monthly Training Trends
SELECT 
  FORMAT_DATE('%Y-%m', DATE(training_date)) AS training_month, 
  COUNT(*) AS training_count 
FROM trainings.trainings 
GROUP BY training_month 
ORDER BY training_count DESC;

-- 5. Book Distribution by Region & Trainer
SELECT 
  governorate, 
  region, 
  SUM(copies_received) AS total_copies 
FROM trainings.book_distribution 
GROUP BY governorate, region 
ORDER BY total_copies DESC;
```
## 📈 Dashboard Preview
<img width="1067" height="506" alt="image" src="https://github.com/user-attachments/assets/31f4ff87-a03f-4e9d-87de-573ca481e9ac" />

## 💡 Key Insights
* **Enrollment Scale & Demographics:** Analyzed a total of **300 trainees** across multiple nationalities and gender distributions to identify primary participant segments.
* **Trainer Productivity:** Tracked report submissions and material distribution (`book_distribution`) per trainer to highlight top-performing instructors.
* **Seasonal Trends:** Monitored monthly training frequencies (`training_month`) to identify peak operational periods and resource demand.



## 📂 Dataset Files
The raw CSV and processed dataset files (`trainers.csv`, `trainees.csv`, `trainings.csv`, `reports.csv`, `book_distribution.csv`) used for this analytics dashboard are included in this repository.

