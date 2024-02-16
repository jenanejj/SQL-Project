Which country has the most visitors that generates the most revenue: 

SQL Queries: 

SELECT *, 
ROW_NUMBER() OVER (PARTITION BY country) AS row_num
FROM ecommerce 
WHERE "totalTransactionRevenue" IS NOT NULL
ORDER BY "totalTransactionRevenue" DESC

Answer: 

United States 


Question 2: 

SQL Queries:

Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
