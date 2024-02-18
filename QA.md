What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it.  

Step 1: Data Profiling (checking for NULL and unique values)

I used the following queries to double check if columns in the table contain NULL values: 

SELECT "productRefundAmount" 
FROM ecommerce
WHERE "productRefundAmount" IS NOT NULL --contain only NULL values

SELECT "transactions"
FROM ecommerce
WHERE "transactions" IS NOT NULL --returned only 81 rows (mostly NULL values) 

Step 2: Data Validation ( check for missing data or duplicate data)

The userid column in the analytics table should be a primary key, as we want to track how many users are purchasing what items. I used this query for the QA: 

SELECT userid 
FROM analytics_1
WHERE userid IS NOT NULL 

If there are no rows returned, then the QA test is passed. If rows are returned, then the QA test is failed. 

I checked to see if the "sku" column in the products table has duplicate rows: 

SELECT "sku", COUNT(*)
FROM products
GROUP BY "sku"
HAVING COUNT(*) > 1; 



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


Step 3: Data Cleaning 

The "sku" column, the data is in different format with values in different lengths so I used the CASE WHEN column to try to create a singular format. 

SELECT *, 
  CASE 
    WHEN LENGTH("sku") = 7 THEN LPAD("sku", 13, '0')
    ELSE "sku"
  END as standardized_productsku
FROM products;
