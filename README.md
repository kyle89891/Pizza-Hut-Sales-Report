# Pizza-Hut-Sales-Report
Thrilled to share that I've recently had the opportunity to create a comprehensive Power BI dashboard report focusing on Pizza Hut sales data! 📈

Overview
This repository provides a detailed guide and resources for creating an insightful Power BI dashboard report focused on Pizza Hut sales data. Leveraging the advanced features of Power BI, we aim to offer stakeholders a comprehensive view of sales performance metrics, customer engagement, and operational efficiency across various outlets.

#Queries-
A. KPI’s
1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
 
2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
 
3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
 
B. Daily Trend for Total Orders
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)

 
C. Monthly Trend for Orders
select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)Output
 
D. % of Sales by Pizza Category
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
 
E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size

F. Total Pizzas Sold by Pizza Category
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
 
G. Top 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
 
H. Bottom 5 Pizzas by Revenue
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
 
I. Top 5 Pizzas by Quantity
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
 
J. Bottom 5 Pizzas by Quantity
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC

 



K. Top 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
 
L. Borrom 5 Pizzas by Total Orders
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
 




Features
1. Dynamic Visualizations
Intuitive graphs showcasing sales trends over different time frames: daily, weekly, monthly, and annually.
2. Geo-Mapping Capabilities
Visualization of Pizza Hut outlets' sales performance across different regions, enabling insights into regional sales dynamics.
3. Product Performance Analytics
Detailed analysis of top-selling pizzas, sides, and beverages, aiding in inventory management and targeted marketing strategies.
4. Customer Segmentation
Advanced customer analytics for segmenting the audience based on purchasing behavior, facilitating targeted promotional campaigns and enhanced customer experiences.
5. Real-Time Data Syncing
Integration of real-time data feeds to ensure stakeholders have access to up-to-date sales figures and performance metrics.

Acknowledgments
Special thanks to the Power BI community for sharing insights, tutorials, and best practices.
![Screenshot (246)](https://github.com/kyle89891/Pizza-Hut-Sales-Report/assets/81356431/17703967-1d8a-41a6-947a-f27b5447c23f)
