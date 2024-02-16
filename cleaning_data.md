What issues will you address by cleaning the data?





Queries:
Below, provide the SQL queries you used to clean your data. 

I retrieved sample data from columns in each table:

SELECT DISTINCT("units_sold") FROM analytics_1

SELECT * FROM analytics_1 LIMIT 100

I checked columns that seemed to contain a lot of NULL values, and double checked if the entire column is NULL or not:

SELECT DISTINCT("units_sold") FROM analytics_1

I wanted to check for outliers:

SELECT "unit_price", COUNT("unit_price") FROM analytics_1 GROUP BY "unit_price" 


I checked columns that seemed to contain a lot of NULL values, and double checked if the entire column is NULL or not: 

SELECT DISTINCT("units_sold")
FROM analytics_1  

I wanted to check if there were primary keys in each table: 

SELECT COUNT(*), "fullVisitorId"
FROM ecommerce
GROUP BY "fullVisitorId"
ORDER BY 1 DESC   

I divided the unit_price column in the analytics table by 1,000,000 and converted it to INT datatype: 

SELECT *, (CAST("unit_price" AS INT)/1000000) AS unitpricedivided 
FROM "analytics_1"

It looked like I can link the productSKU on the sales_report table and sales_by_sku, but I got an error- so I ran this code: 

SELECT DISTINCT "productSKU" FROM sales_by_sku
WHERE "productSKU" NOT IN (SELECT DISTINCT "productSKU" FROM sales_report); 

The rows are not linked on each row, so I confirmed they cannot be Primary Key or Foreign Key. 

I wanted to review columns in tables that only contained NULL values and replace it with relevant information. For exacmple, in the analytics table, the userid column only contains NULL values. So, I created this query: 

SELECT *,
CASE 
WHEN userid IS NULL THEN "analytics_1"."visitId"
ELSE userid
END AS user_info
FROM analytics_1;


