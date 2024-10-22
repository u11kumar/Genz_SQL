# Genz_SQL

# 📊 SQL Queries for Gen Z Career Aspirations Project

Welcome to the **Gen Z Career Aspirations Project** repository! 🎉 This project aims to answer various business questions related to the career aspirations of Gen Z using **SQL queries** on a dataset from **India**.

Below, you’ll find the SQL commands for each business question. Feel free to **copy and paste** these queries into your SQL editor to explore the data! 😊

---

## 1️⃣ Gender Distribution of Respondents from India

```sql
SELECT 
    gender,
    COUNT(*) AS count
FROM
    book1
WHERE
    country = 'India'
GROUP BY 
    gender;
```

---

## 2️⃣ Percentage of Respondents Interested in Education Abroad & Sponsorship

```sql
SELECT
    'India' AS country,
    SUM(CASE WHEN 'Purse Foreign Higher Education' = 'Need Sponsor' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS 'Need Sponsor (%)',
    SUM(CASE WHEN 'Purse Foreign Higher Education' = 'No' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS 'No (%)',
    SUM(CASE WHEN 'Purse Foreign Higher Education' = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS 'Yes (%)',
    100.0 AS 'Grand total(%)'
FROM 
    book1
WHERE   
    country = 'India';
```

---

## 3️⃣ Top 6 Influences on Career Aspirations in India

```sql
SELECT
    gender,
    'Influencing Factors',
    COUNT(*) AS influence_count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY 'Influencing Factors'
ORDER BY influence_count DESC
LIMIT 6;
```

---

## 4️⃣ Career Aspiration Influences by Gender

```sql
SELECT
    gender,
    'Influencing Factors',
    COUNT(*) AS influence_count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY gender, 'Influencing Factors'
ORDER BY gender, influence_count DESC;
```

---

## 5️⃣ Willingness to Work for a Company for at Least 3 Years

```sql
SELECT
    '3-year Commitment',
    COUNT(*) AS count,
    (COUNT(*) * 100.0 / (SELECT COUNT(*) FROM book1 WHERE country = 'India')) AS percentage
FROM 
    book1 
WHERE 
    country = 'India'
GROUP BY '3-year Commitment';
```

---

## 6️⃣ Respondents Who Prefer Socially Impactful Companies

```sql
SELECT
    gender,
    CASE
        WHEN 'Rate company without social mission' BETWEEN 1 AND 4 THEN 'Yes'
        WHEN 'Rate company without social mission' BETWEEN 4 AND 6 THEN 'Maybe'
        WHEN 'Rate company without social mission' BETWEEN 6 AND 10 THEN 'No'
    END AS preference,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY preference;
```

---

## 7️⃣ Preference for Socially Impactful Companies by Gender

```sql
SELECT
    gender,
    CASE
        WHEN 'Rate company without social mission' BETWEEN 1 AND 4 THEN 'Yes'
        WHEN 'Rate company without social mission' BETWEEN 4 AND 6 THEN 'Maybe'
        WHEN 'Rate company without social mission' BETWEEN 6 AND 10 THEN 'No'
    END AS preference,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY gender, preference
ORDER BY gender, preference;
```

---

## 8️⃣ Minimum Expected Salary in the First Three Years

```sql
SELECT
    'Minimum Monthly Salary (first 3 years)' AS expected_salary,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY 'Minimum Monthly Salary (first 3 years)'
ORDER BY CAST('Minimum Monthly Salary (first 3 years)' AS INTEGER);
```

---

## 9️⃣ Expected Minimum Monthly Salary In-Hand

```sql
SELECT
    'In-hand Salary' AS salary_range,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India'
GROUP BY 'In-hand Salary'
ORDER BY 
    CASE 
        WHEN 'In-hand Salary' = '5k to 10k' THEN 1
        WHEN 'In-hand Salary' = '11k to 20k' THEN 2
        WHEN 'In-hand Salary' = '21k to 30k' THEN 3
        WHEN 'In-hand Salary' = '31k to 50k' THEN 4
        WHEN 'In-hand Salary' = '>50k' THEN 5
        ELSE 6
    END;
```

---

## 🔟 Percentage of Respondents Who Prefer Remote Work

```sql
SELECT
    (COUNT(CASE WHEN 'Preferred Environment' = 'Remote' THEN 1 END) * 100.0 / COUNT(*)) AS percentage_prefer_remote
FROM 
    book1
WHERE 
    country = 'India';
```

---

## 🔟+1 Preferred Number of Daily Work Hours

```sql
SELECT
    'Daily preferred working hours' AS preferred_hours,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India' AND 'Daily preferred working hours' != 'N/A'
GROUP BY 'Daily preferred working hours'
ORDER BY CAST('Daily preferred working hours' AS INTEGER);
```

---

## 🔟+2 Common Work Frustrations Among Respondents

```sql
SELECT
    gender,
    'What would frustrate you at work?' AS frustration,
    COUNT(*) AS count
FROM 
    book1
WHERE 
    country = 'India' AND 'What would frustrate you at work?' != 'N/A'
GROUP BY 'What would frustrate you at work?'
ORDER BY count DESC;
```

---

## 📄 More SQL Queries

Find the rest of the queries in the repository to explore **work-life balance** interventions, **willingness to work under abusive managers**, and **expected salaries after five years**. 💼

---

### 💡 How to Use

1. **Clone the repository** or **download** the SQL query file.
2. Copy the queries from here and **run them in your SQL editor**.
3. Explore the dataset and gain insights into **Gen Z’s career aspirations**! ✨

---

**Thank you for visiting!** 😊
