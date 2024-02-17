What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it. 

The userid column in the analytics table should be a primary key, as we want to track how many users are purchasing what items. I used this query for the QA: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL 

If there are no rows returned, then the QA test is passed. If rows are returned, then the QA test is failed. 

I checked columns if they contain NULLS: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL 

I noticed that productSKU column in the ecommerce table and productSKU column seemed to be the same. So, I tried to link them to double check the referential integrity of the data.  

I want to make sure the data reliable. I am assuming that the productSKU in sales_report table and sales_by_SKU to have the same information: 

I used this query to check reliability:

SELECT COUNT("productSKU"), "productSKU"
FROM sales_by_sku
GROUP BY "productSKU" 

SELECT COUNT("productSKU"), "productSKU"
FROM sales_report
GROUP BY "productSKU"  

The rows returned have different numbers, so I am assuming there are data missing. 
