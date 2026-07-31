# 📊 SQL Data Analytics Project

## Overview

This project explores the data analyst job market using SQL. By analyzing a real-world dataset of job postings, I examined salary trends, employer requirements, and the technical skills that are most valuable for aspiring data analysts.

The project focuses on answering practical questions such as:

* Which data analyst jobs offer the highest salaries?
* What skills do employers expect for high-paying roles?
* Which technical skills appear most frequently in job postings?
* Which skills are linked to higher average salaries?
* What skills provide the best balance between demand and earning potential?

All SQL queries used for this analysis are available in the **project_sql** folder.

---

# Project Background

As part of my SQL learning journey, I wanted to apply SQL concepts to a realistic business dataset rather than only practicing isolated queries.

Using a dataset containing job postings, salary information, company details, locations, and required skills, I performed exploratory analysis to better understand the current data analyst job market.

The project allowed me to practice SQL while answering questions that are useful for anyone planning a career in data analytics.

---

# Dataset

The dataset includes information such as:

* Job titles
* Company names
* Salary details
* Job locations
* Remote work availability
* Required technical skills

This data was provided as part of the SQL learning course and serves as the foundation for all analyses in this project.

---

# Tools Used

* **SQL** – Querying and analyzing data
* **PostgreSQL** – Database management system
* **Visual Studio Code** – SQL development environment
* **Git & GitHub** – Version control and project hosting

---

# Project Analysis

## 1. Highest Paying Data Analyst Jobs

This analysis identifies the highest-paying remote Data Analyst positions with available salary information. It highlights the organizations offering competitive salaries and the variety of senior analytical roles available.

| Rank | Job Title                         | Company           | Salary ($) |
| ---: | --------------------------------- | ----------------- | ---------: |
|    1 | Data Analyst                      | SmartAsset        |    650,000 |
|    2 | Director of Analytics             | Meta              |    336,500 |
|    3 | Associate Director, Data Insights | AT&T              |    255,829 |
|    4 | Principal Data Analyst            | Pinterest         |    232,423 |
|    5 | Data Analytics Lead               | UclaHealthCareers |    217,000 |
|    6 | Data Analyst                      | SmartAsset        |    205,000 |
|    7 | Director, Data Analyst            | Motional          |    189,309 |
|    8 | Principal Data Analyst            | SmartAsset        |    186,000 |
|    9 | ERM Data Analyst                  | Get It Recruit    |    184,000 |
|   10 | Data Analyst                      | Get It Recruit    |    184,000 |

---

## 2. Skills Required for High-Paying Jobs

After identifying the top-paying positions, I analyzed the skills required for those roles. SQL, Python, and Tableau consistently appeared across the highest-paying job postings, demonstrating their importance in advanced analytics roles.

| Skill     | Number of Top 10 Jobs |
| --------- | --------------------: |
| SQL       |                     8 |
| Python    |                     7 |
| Tableau   |                     6 |
| R         |                     4 |
| Snowflake |                     3 |
| Excel     |                     3 |
| Pandas    |                     2 |

---

## 3. Most In-Demand Skills

This analysis identifies the skills that appear most frequently in Data Analyst job postings.

| Skill    | Demand Count |
| -------- | -----------: |
| SQL      |         7291 |
| Excel    |         4611 |
| Python   |         4330 |
| Tableau  |         3745 |
| Power BI |         2609 |

The results show that SQL continues to be the most requested skill, followed by Excel, Python, Tableau, and Power BI.

---

## 4. Skills Associated with Higher Salaries

To understand which technical skills command the highest salaries, I calculated the average salary associated with each skill.

| Skill         | Average Salary ($) |
| ------------- | -----------------: |
| PySpark       |            208,172 |
| Bitbucket     |            189,155 |
| Couchbase     |            160,515 |
| Watson        |            160,515 |
| DataRobot     |            155,486 |
| GitLab        |            154,500 |
| Swift         |            153,750 |
| Jupyter       |            152,777 |
| Pandas        |            151,821 |
| Elasticsearch |            145,000 |

These technologies are primarily associated with cloud computing, big data processing, machine learning, and data engineering, making them highly valuable in today's analytics industry.

---

## 5. Most Valuable Skills to Learn

This analysis combines both salary and demand to identify skills that provide the best return for aspiring data analysts.

| Skill      | Demand Count | Average Salary ($) |
| ---------- | -----------: | -----------------: |
| Go         |           27 |            115,320 |
| Confluence |           11 |            114,210 |
| Hadoop     |           22 |            113,193 |
| Snowflake  |           37 |            112,948 |
| Azure      |           34 |            111,225 |
| BigQuery   |           13 |            109,654 |
| AWS        |           32 |            108,317 |
| Java       |           17 |            106,906 |
| SSIS       |           12 |            106,683 |
| Jira       |           20 |            104,918 |

These results suggest that developing expertise in cloud platforms, big data technologies, and modern analytics tools can significantly improve both employability and earning potential.

---

# Key Findings

* Remote Data Analyst positions can offer exceptionally high salaries.
* SQL remains the most important technical skill for Data Analysts.
* Python and Tableau are consistently required across high-paying roles.
* Cloud technologies and big data tools are associated with higher salaries.
* Combining high-demand skills with specialized technologies provides the greatest career opportunities.

---

# What I Learned

This project strengthened my SQL skills by allowing me to work with a real-world dataset. Throughout the analysis, I gained practical experience with:

* Writing complex SQL queries
* Using JOINs to combine multiple tables
* Working with Common Table Expressions (CTEs)
* Applying aggregate functions such as COUNT() and AVG()
* Filtering and sorting large datasets
* Using GROUP BY, HAVING, ORDER BY, and LIMIT
* Translating business questions into SQL queries that generate meaningful insights

---

# Conclusion

Completing this project gave me hands-on experience using SQL to analyze a real-world dataset and answer practical business questions. It strengthened both my SQL knowledge and my analytical thinking while providing valuable insights into the current Data Analyst job market.

This project represents an important milestone in my journey toward becoming a Data Analyst and demonstrates my ability to extract meaningful insights from data using SQL.
