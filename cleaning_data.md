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
