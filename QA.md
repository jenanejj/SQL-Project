What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it. 

The userid column in the analytics table should be a primary key, as we want to track how many users are purchasing what items. I used this query for the QA: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL

I checked columns if they contain NULLS: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL 

I noticed that productSKU column in the ecommerce table and productSKU column seemed to be the same. So, I tried to link them to double check the referential integrity of the data. 
