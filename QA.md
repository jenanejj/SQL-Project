What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it. 

I checked columns if they contain NULLS: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL
