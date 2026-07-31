# 📊 SQL Data Analytics Project

## Overview

This project explores the Data Analyst job market using SQL. By analyzing a real-world dataset of job postings, I investigated salary trends, in-demand skills, and the technologies that provide the greatest career opportunities for aspiring Data Analysts.

The project answers the following business questions:

* What are the highest-paying Data Analyst jobs?
* Which skills are required for these high-paying positions?
* What are the most in-demand skills for Data Analysts?
* Which skills are associated with the highest salaries?
* Which skills offer the best balance between demand and earning potential?

---

# Background

This project was completed as part of my SQL learning journey. It allowed me to apply SQL concepts to a real-world dataset containing job postings, company information, salaries, locations, and technical skills.

The objective was not only to practice SQL syntax but also to solve practical business questions using data analysis techniques.

---

# Tools Used

* **SQL**
* **PostgreSQL**
* **Visual Studio Code**
* **Git & GitHub**

---

# Analysis

## 1. Top Paying Data Analyst Jobs

### SQL Query

```sql
SELECT
    job_id,
    job_title,
    job_location,
    job_schedule_type,
    salary_year_avg,
    job_posted_date,
    name AS company_name
FROM job_postings_fact
LEFT JOIN company_dim
    ON job_postings_fact.company_id = company_dim.company_id
WHERE
    job_title_short = 'Data Analyst'
    AND job_location = 'Anywhere'
    AND salary_year_avg IS NOT NULL
ORDER BY salary_year_avg DESC
LIMIT 10;
```

### Results

| Rank | Job Title                         | Company        | Salary ($) |
| ---: | --------------------------------- | -------------- | ---------: |
|    1 | Data Analyst                      | SmartAsset     |    650,000 |
|    2 | Director of Analytics             | Meta           |    336,500 |
|    3 | Associate Director, Data Insights | AT&T           |    255,829 |
|    4 | Principal Data Analyst            | Pinterest      |    232,423 |
|    5 | Data Analytics Lead               | UCLA Health    |    217,000 |
|    6 | Data Analyst                      | SmartAsset     |    205,000 |
|    7 | Director, Data Analyst            | Motional       |    189,309 |
|    8 | Principal Data Analyst            | SmartAsset     |    186,000 |
|    9 | ERM Data Analyst                  | Get It Recruit |    184,000 |
|   10 | Data Analyst                      | Get It Recruit |    184,000 |

### Key Insights

* Remote Data Analyst positions offer highly competitive salaries.
* Senior analytics positions command the highest compensation.
* Companies across multiple industries actively invest in experienced analytics professionals.

---

## 2. Skills Required for Top Paying Jobs

### SQL Query

```sql
WITH top_paying_jobs AS (
    SELECT
        job_id,
        job_title,
        salary_year_avg,
        name AS company_name
    FROM job_postings_fact
    LEFT JOIN company_dim
        ON job_postings_fact.company_id = company_dim.company_id
    WHERE
        job_title_short = 'Data Analyst'
        AND job_location = 'Anywhere'
        AND salary_year_avg IS NOT NULL
    ORDER BY salary_year_avg DESC
    LIMIT 10
)

SELECT
    top_paying_jobs.*,
    skills
FROM top_paying_jobs
INNER JOIN skills_job_dim
    ON top_paying_jobs.job_id = skills_job_dim.job_id
INNER JOIN skills_dim
    ON skills_job_dim.skill_id = skills_dim.skill_id
ORDER BY salary_year_avg DESC;
```

### Results

| Skill     | Number of Top 10 Jobs |
| --------- | --------------------: |
| SQL       |                     8 |
| Python    |                     7 |
| Tableau   |                     6 |
| R         |                     4 |
| Snowflake |                     3 |
| Excel     |                     3 |
| Pandas    |                     2 |

### Key Insights

* SQL appears in most of the highest-paying job postings.
* Python and Tableau are also highly valued by employers.
* Employers prefer candidates with a combination of programming and visualization skills.

---

## 3. Most In-Demand Skills

### SQL Query

```sql
SELECT
    skills,
    COUNT(skills_job_dim.job_id) AS demand_count
FROM job_postings_fact
INNER JOIN skills_job_dim
    ON job_postings_fact.job_id = skills_job_dim.job_id
INNER JOIN skills_dim
    ON skills_job_dim.skill_id = skills_dim.skill_id
WHERE
    job_title_short = 'Data Analyst'
    AND job_work_from_home = TRUE
GROUP BY skills
ORDER BY demand_count DESC
LIMIT 5;
```

### Results

| Skill    | Demand Count |
| -------- | -----------: |
| SQL      |         7291 |
| Excel    |         4611 |
| Python   |         4330 |
| Tableau  |         3745 |
| Power BI |         2609 |

### Key Insights

* SQL remains the most requested technical skill.
* Excel continues to be widely used in analytics roles.
* Python, Tableau, and Power BI are essential tools for modern Data Analysts.

---

## 4. Highest Paying Skills

### SQL Query

```sql
SELECT
    skills,
    ROUND(AVG(salary_year_avg),0) AS avg_salary
FROM job_postings_fact
INNER JOIN skills_job_dim
    ON job_postings_fact.job_id = skills_job_dim.job_id
INNER JOIN skills_dim
    ON skills_job_dim.skill_id = skills_dim.skill_id
WHERE
    job_title_short = 'Data Analyst'
    AND salary_year_avg IS NOT NULL
    AND job_work_from_home = TRUE
GROUP BY skills
ORDER BY avg_salary DESC
LIMIT 10;
```

### Results

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

### Key Insights

* Big data technologies command the highest salaries.
* Machine learning and cloud-related skills significantly increase earning potential.
* Data engineering tools are increasingly valuable in analytics roles.

---

## 5. Most Optimal Skills to Learn

### SQL Query

```sql
WITH skills_demand AS (
    SELECT
        skills_dim.skill_id,
        skills,
        COUNT(skills_job_dim.job_id) AS demand_count
    FROM job_postings_fact
    INNER JOIN skills_job_dim
        ON job_postings_fact.job_id = skills_job_dim.job_id
    INNER JOIN skills_dim
        ON skills_job_dim.skill_id = skills_dim.skill_id
    WHERE
        job_title_short = 'Data Analyst'
        AND salary_year_avg IS NOT NULL
        AND job_work_from_home = TRUE
    GROUP BY
        skills_dim.skill_id,
        skills
),
average_salary AS (
    SELECT
        skills_dim.skill_id,
        skills,
        ROUND(AVG(salary_year_avg),0) AS avg_salary
    FROM job_postings_fact
    INNER JOIN skills_job_dim
        ON job_postings_fact.job_id = skills_job_dim.job_id
    INNER JOIN skills_dim
        ON skills_job_dim.skill_id = skills_dim.skill_id
    WHERE
        job_title_short = 'Data Analyst'
        AND salary_year_avg IS NOT NULL
        AND job_work_from_home = TRUE
    GROUP BY
        skills_dim.skill_id,
        skills
)

SELECT
    skills_demand.skills,
    demand_count,
    avg_salary
FROM skills_demand
INNER JOIN average_salary
    ON skills_demand.skill_id = average_salary.skill_id
WHERE demand_count > 10
ORDER BY
    avg_salary DESC,
    demand_count DESC
LIMIT 25;
```

### Results

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

### Key Insights

* Cloud technologies offer an excellent combination of salary and demand.
* SQL remains the foundation for a successful Data Analytics career.
* Learning cloud platforms and big data tools can significantly improve career prospects.

---

# What I Learned

Throughout this project, I strengthened my SQL skills by working with a real-world dataset and applying concepts such as:

* Complex SQL queries
* JOIN operations
* Common Table Expressions (CTEs)
* Aggregate functions
* GROUP BY and HAVING
* Sorting and filtering data
* Data-driven problem solving

---

# Conclusion

This project provided valuable hands-on experience using SQL to solve real business problems. It enhanced my technical skills while improving my ability to analyze data, identify trends, and communicate meaningful insights. The project represents an important milestone in my journey toward becoming a Data Analyst.
