Which country has the most visitors in countries generates the most revenue: 

SQL Queries: 

SELECT *, 
ROW_NUMBER() OVER (PARTITION BY country ORDER BY "totalTransactionRevenue" DESC ) AS row_num
FROM ecommerce 
WHERE "totalTransactionRevenue" IS NOT NULL
--I'm grouping each country by transactions that are NOT NULL from highest to lowest

Answer: 

Australia 


Question 2: Which product generated the most revenue? 

SQL Queries:

SELECT *, 
ROW_NUMBER() OVER (PARTITION BY "v2ProductCategory") AS prod_rev
FROM ecommerce 
WHERE "totalTransactionRevenue" IS NOT NULL
ORDER BY "totalTransactionRevenue" DESC

Answer:

Waze



Question 3: Are there any products that were not ordered by any customers?

SQL Queries:

SELECT * 
FROM products AS p 
JOIN ecommerce AS e
ON p."sku" = e."productSKU"
WHERE "orderedquantity" = 0


Answer:Productname is "Womens Colorblock Tee White"



Question 4: Which product has the most products in stock?

SQL Queries:

SELECT * , (CAST("stockLevel" AS INT)- ss."total_ordered") AS remaining 
FROM sales_by_sku AS ss
JOIN sales_report AS sr
ON ss."productSKU" = sr."productSKU"
ORDER BY remaining DESC

Answer:

" 22 oz Water Bottle" and it has 19655 in stock

Question 5: Which product has the most revenue? 

SQL Queries:
SELECT "v2ProductName", "v2ProductCategory", "pageTitle", "revenue"
FROM analytics_1 AS an
JOIN ecommerce AS ec
ON an."visitId"= ec."visitId"
WHERE revenue IS NOT NULL
ORDER BY revenue DESC

Answer: ""SPF-15 Slim & Slender Lip Balm"
