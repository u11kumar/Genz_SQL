1. What is the gender distribution of respondents from India?

````select
    gender,
    count(*) as count
from
    book1
where
    country = 'India'
group by
    gender;  ```

---------------
2. What percentage of respondents from India are interested in education abroad and sponsorship?

``` select
    'India' as country,
        sum(case when 'Purse Foregin Higher Education' = 'Need Sponsor' then 1 else 0 end)*100.0/count(*) as 'Need Sponsor (%)',
        sum(case when 'Purse Foregin Higher Education' = 'No' then 1 else 0 end)*100.0/count(*) as 'No (%)',
        sum(case when 'Purse Foregin Higher Education' = 'Yes' then 1 else 0 end)*100.0/count(*) as 'Yes (%)',
        100.0 as 'Grand total(%)'
from
    book1
where
    country = 'India';  ```

---------------
3. What are the 6 top influences on career aspirations for respondents in India?

``` select
    gender,
    'Influencing Factors',
    count(*) as influence_count
from
    book1
where
    country = 'India'
group by 'Influencing Factors'
order by influence_count desc
limit 6;  ```


---------------
4. How do career aspiration influences vary by gender in India?

``` select
    gender,
    'Influencing Factors',
    count(*) as influence_count
from
    book1
where
    country = 'India'
group by gender,'Influencing Factors'
order by gender,influence_count desc;  ```

---------------
5. What percentage of respondents are willing to work for a company for at least 3 years?

``` select
    '3-year Commitment',
    count(*) as count,
    (count(*)*100.0/ (``` select count(*) from book1 where country ='India')) as percentage
from
    book1
where
    country ='India'
group by '3-year Commitment';  ```

---------------
6. How many respondents prefer to work for socially impactful companies?

``` select
    gender,
    case
        when 'Rate company without social mission' between 1 and 4  then 'Yes'
        when 'Rate company without social mission' between 4 and 6 then 'Maybe'
        when 'Rate company without social mission' between 6 and 10 then 'No'
    end as preference,
    count(*) as count
from
    book1
where
    country = 'India'
group by preference;  ```

---------------
7. How does the preference for socially impactful companies vary by gender?

``` select
    gender,
    case
        when 'Rate company without social mission' between 1 and 4  then 'Yes'
        when 'Rate company without social mission' between 4 and 6 then 'Maybe'
        when 'Rate company without social mission' between 6 and 10 then 'No'
    end as preference,
    count(*) as count
from
    book1
where
    country = 'India'
group by gender,preference
order by gender,preference;  ```

---------------
8. What is the distribution of minimum expected salary in the first three years among respondents?

``` select
    'Minimum Monthly Salary (first 3years)' as expected_salary,
    count(*) as count
from
    book1
where
    country = 'India'
group by 'Minimum Monthly Salary (first 3years)'
order by cast('Minimum Monthly Salary (first 3years)' as integer);  ```

---------------
9. What is the expected minimum monthly salary in hand?

``` select
    'In-hand Salary' as salary_range,
    count(*) as count
from
    book1
where
    country='India'
group by 'In-hand Salary'
order by
    case
        when 'In-hand Salary' = '5k to 10k' then 1
        when 'In-hand Salary' = '11k to 20k' then 3
        when 'In-hand Salary' = '21k to 30k' then 4
        when 'In-hand Salary' = '31k to 50k' then 2
        when 'In-hand Salary' = '>50k' then 5
        else 6
    end;  ```

---------------
10. What percentage of respondents prefer remote working?

``` select
    (count(case when 'Preferred Environment'='Remote' then 1 end)*100.0 / count(*)) as percentage_prefer_remote
from
    book1
where
    country = 'India';  ```

---------------
11. What is the preferred number of daily work hours?

``` select
    'Daily preferred working hours' as preferred_hours,
    count(*) as count
from
    book1
where
    country = 'India' and 'Daily preferred working hours' != 'N/A'
group by 'Daily preferred working hours'
order by
cast('Daily preferred working hours' as integer);  ```


---------------
12. What are the common work frustrations among respondents?

``` select
    gender,
    'What would frustate you at work ?' as frustration,
    count(*) as count
from
    book1
where
    country = 'India' and 'What would frustate you at work ?' != 'N/A'
group by 'What would frustate you at work ?'
order by count desc;  ```

---------------
13. How does the need for work-life balance interventions vary by gender?

``` select
    gender,
    'Number of week off for a healthy work-life balance?' as weeks_off,
    count(*) as count
from
    book1
where
    country = 'India' and book1.'Number of week off for a healthy work-life balance?' != 'N/A'
group by gender,'Number of week off for a healthy work-life balance?'
order by gender,weeks_off;  ```

---------------
14. How many respondents are willing to work under an abusive manager?

``` select
    'Work for an abusive maanger' as willingness,
    count(*) as count
from
    book1
where
    country = 'India' and 'Work for an abusive maanger' != 'N/A'
group by 'Work for an abusive maanger';  ```

---------------
15. What is the distribution of minimum expected salary after five years?

``` select
    'Minimum monthly salary (after 5years)' as expected_salary
    count(*) as count
from
    book1
where
    country = 'India'
group by 'Minimum monthly salary (after 5years)'
order by
    case
        when 'Minimum monthly salary (after 5years)' = 'less than 70k' then 1
        when 'Minimum monthly salary (after 5years)' = '71k to 110k' then 2
        when 'Minimum monthly salary (after 5years)' = '111k to 150k' then 3
        when 'Minimum monthly salary (after 5years)' = '>151k' then 4
        else 5
    end;  ```
---------------
16. What are the remote working preferences by gender?

``` select
    gender,
    'Preferred Environment' as remote_work_preference,
    count(*) as count
from
    book1
where
    country = 'India'
group by gender,'Preferred Environment'
order by gender,remote_work_preference;  ```

---------------
17. What are the top work frustrations for each gender?

``` select
    gender,
    'What would frustate you at work ?' as frustration,
    count(*) as count
from
    book1
where
    country = 'India' and 'What would frustate you at work ?' != 'N/A'
group by gender,'What would frustate you at work ?'
order by gender,count desc;  ```

---------------
18. What factors boost work happiness and productivity for respondents?

``` select
    'Factors for happier and productive at work' as factor,
    count(*) as count
from
    book1
where
    country = 'India' and 'Factors for happier and productive at work' != 'N/A'
group by 'Factors for happier and productive at work'
order by count desc;  ```

---------------
19. What percentage of respondents need sponsorship for education abroad?

``` select
    'Purse Foregin Higher Education' as sponsorship_need,
    count(*) as count,
    (count(*)*100.0 / (``` select count(*) from book1 where country='India'))as percentage
from
    book1
where
    country = 'India'
group by 'Purse Foregin Higher Education';  ```
````
