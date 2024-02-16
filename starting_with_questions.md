Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

SELECT "country", "city", "transactionRevenue"
FROM ecommerce 
WHERE "transactionRevenue" IS NOT NULL
GROUP BY "city", "country", "transactionRevenue"


Answer:

"United States"	"Sunnyvale"	"200000000"
"United States"	"not available in demo dataset"	"1005500000"
"United States"	"not available in demo dataset"	"1015480000"
"United States"	"not available in demo dataset"	"169970000"


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 

SELECT "visitId", "city", "country", "v2ProductName", AVG("total_ordered") as AVG_ORDERED
FROM ecommerce AS ec
JOIN sales_by_SKU AS ss
ON ec."productSKU" = ss."productSKU"
GROUP BY "city", "country", "v2ProductName", "visitId"
ORDER BY AVG("total_ordered") DESC

Please note: I was not sure if I should use "visitId" or "fullvisitorId" column as I was not sure what the difference was between the columns. So, I made the assumption to include the "visitId". 



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

SELECT "visitId", "city", "country", "v2ProductName", "v2ProductCategory", "totalTransactionRevenue", 
ROW_NUMBER() OVER (PARTITION BY "v2ProductCategory") AS prod_rev
FROM ecommerce AS ec
JOIN sales_by_SKU AS ss
ON ec."productSKU" = ss."productSKU"
WHERE "totalTransactionRevenue" IS NOT NULL
GROUP BY "city", "country", "v2ProductName", "visitId", "v2ProductCategory", "totalTransactionRevenue"


Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

SELECT "visitId", "city", "country", "v2ProductName", "v2ProductCategory", "totalTransactionRevenue", 
ROW_NUMBER() OVER (PARTITION BY "city") AS city_rev
FROM ecommerce AS ec
JOIN sales_by_SKU AS ss
ON ec."productSKU" = ss."productSKU"
WHERE "totalTransactionRevenue" IS NOT NULL
GROUP BY "city", "country", "v2ProductName", "visitId", "v2ProductCategory", "totalTransactionRevenue" 
ORDER BY "totalTransactionRevenue" DESC


Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







