What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it. 

I checked columns if they contain NULLS: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL 

I noticed that productSKU column in the ecommerce table and productSKU column seemed to be the same. So, I tried to link them to double check the integrity of the data. 
