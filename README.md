# Case-Email-Campaign-Performance-anyalsis
# Business and Tech goal
Help the client of our company which is a retail company to test their email campaign's performance, increace their customer's engagement and comapny's total sales.
Analyzing KPIs such as click rate, conversion rate, retention rate and others to seek business opptunities.
# Data model
![email campagin snow flake schema](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/85d95d7f-c129-4823-bcd3-126cddd29f9f)
# some key requirements
1.Based your understanding, please define retention rate, write a SQL query that calculates for Day 10 and Day 30 retention rate for month of September.
 WITH total AS (
    SELECT 
        client_id,
        MIN(activity_date) as first_activity_date -- getting the first activity date for each client
    FROM 
        Activity 
    WHERE 
        activity_date BETWEEN '2019-09-01' AND '2019-09-30'
    GROUP BY 
        client_id
),
activity_10_day AS (
    SELECT 
        a.client_id 
    FROM 
        Activity a
    INNER JOIN 
        cohort c ON a.client_id = c.client_id
    WHERE 
        a.activity_date BETWEEN c.first_activity_date AND c.first_activity_date + INTERVAL '10 day'
),
activity_30_day AS (
    SELECT 
        a.client_id 
    FROM 
        Activity a
    INNER JOIN 
        cohort c ON a.client_id = c.client_id
    WHERE 
        a.activity_date BETWEEN c.first_activity_date AND c.first_activity_date + INTERVAL '30 day'
)
SELECT 
    '10_day_retention' AS retention_type,
    COUNT(DISTINCT c.client_id) AS initial_cohort,
    COUNT(DISTINCT a10.client_id) AS retained_clients,
    COUNT(DISTINCT a10.client_id) / NULLIF(COUNT(DISTINCT c.client_id), 0) * 100.0 AS retention_rate
FROM 
    cohort c
LEFT JOIN 
    activity_10_day a10 ON c.client_id = a10.client_id
UNION ALL
SELECT 
    '30_day_retention' AS retention_type,
    COUNT(DISTINCT c.client_id) AS initial_cohort,
    COUNT(DISTINCT a30.client_id) AS retained_clients,
    COUNT(DISTINCT a30.client_id) / NULLIF(COUNT(DISTINCT c.client_id), 0) * 100.0 AS retention_rate
FROM 
    cohort c
LEFT JOIN 
    activity_30_day a30 ON c.client_id = a30.client_id;
