# LITA_CAPSTONE_PROJECT

### Project Title: Sales Performance Analysis for a Retail Store 

### Project Overview

In today's data-driven world, the ability to interpret and leverage data has become a pivotal skill.For this project,I embarked on an analytical journey to unveil insights through data analysis.I was able to uncover trends and patterns within a diverse dataset.

### Project Objectives

The primary aim of this project was to utilize data analysis techniques to uncover key insights such as top selling products,regional performance and monthly sales trend.By exploring the dataset I sought to:

- Identify key performance indicators(KPIs) that reflect the data's performance.
- Highlight trends and patterns that can inform strategic decisions.
- Provide a comprehensive narrative that translates complex data into understandable insights.

### Data Source

The primary source of data used here is Lita Capstone Dataset.xlsx which was provided by the INCUBATOR HUB as a project work for every student. 

### Methodology
This project employeed a structured approach involving various data analysis tools and techniques:

 - Microsoft excel  [Download Here](https://www.microsoft.com)
   1. for data cleaning
   2. analysis and visualization
 - Structured Query Language (SQL)
   1. for querying
   2. extraction and manipulation of data
 - PowerBI for visualization and report
 - Github for portfolio building.

### Data Cleaning and Preparation

In the initial phase of the data cleaning and preparation,the following actions was performed;
1. data loading and inspections
2. handling missing variables
3. data cleaning and formatting

### Exploratory Data Analysis
EDA involved the exploring of the data to answer some questions about the data such as;
1. Excel:
- Perform an initial exploration of the sales data. Use pivot tables to summarize
total sales by product, region, and month.
- Use Excel formulas to calculate metrics such as average sales per product and
total revenue by region.
- Create any other interesting report
2. SQL:
Hint – You need to load the dataset into your SQL Server environment to write and
validate your queries.
Write queries to extract key insights based on the following questions.
- retrieve the total sales for each product category.
- find the number of sales transactions in each region.
- find the highest-selling product by total sales value.
- calculate total revenue per product.
- calculate monthly sales totals for the current year.
- find the top 5 customers by total purchase amount.
- calculate the percentage of total sales contributed by each region.
- identify products with no sales in the last quarter.

3. Power BI:
- Create a dashboard that visualizes the insights found in Excel and SQL. The
dashboard should include a sales overview, top-performing products, and
regional breakdowns.

### Results and Interpretation

<img width="952" alt="Excel 1" src="https://github.com/user-attachments/assets/67e7a74a-5d6a-4651-83cf-0bcbb1805b5d">

These pivot table summarizes the total sales by product,region,month and Average sales per product,total revenue by region.

I was able to deduce that the top selling product is 'shoe' with a value of 613,380 and the least selling product is 'socks' with a value of 180,785.Also the 'South' region has the highest revenue  which is 927,820 while the 'west' region has the least revenue has 300,345.In the year 2023,Sales was made in the month of January to December and  February has the higest revenue of '247,500' while April has the slowest sales with revenue of '7,425' and the total revenue for 2023 is 1,105,330. While in 2024 sales was made in the month of February to July, February is also the highest sales month with revenue of '298,800' and July the slow sales month with revenue of '37,200', the total revenue for 2024 is 995,760 and both year totals a revenue of 2,101,090.

Excel formula was also used to calculate average sales per product  and total revenue by region,the formular used is;

 =AVERAGEIF(C2:C9922,C2,H2:H9923) SOCKS = 122 

=AVERAGEIF(C2:C9922,C9899,H2:H9923) GLOVES  = 200

=AVERAGEIF(C2:C9922,C6448,H2:H9923) HAT = 159

=AVERAGEIF(C2:C9922,C4960,H2:H9923) JACKET =140

=AVERAGEIF(C2:C9922,C3473,H2:H9923) SHIRT = 327

=AVERAGEIF(C2:C9922,C1486,H2:H9923) SHOES  = 309

After sorting my product column,I was able to calculate average for each product

=SUM(H2:H9922) = 2101090 as Total revenue


```SQL

---1 Total sales for each Product category----
SELECT Product,SUM(Quantity * UnitPrice) AS Total_sales 
FROM [dbo].[LITACapstoneDataset]
GROUP BY Product
ORDER BY 2 DESC;

----2 Number of sales Transaction in each Region---
SELECT Region,COUNT(Revenue) AS Number_of_Sales
FROM [dbo].[LITACapstoneDataset]
GROUP BY Region
ORDER BY 2 DESC;

---3 Highest selling Product by Total sales value---
SELECT Product,SUM(Revenue) AS Total_sales 
FROM [dbo].[LITACapstoneDataset]
GROUP BY Product
ORDER BY Total_sales DESC;

--- 4 Total Revenue per Product---
SELECT Product, SUM(Revenue) AS Total_Revenue
FROM [dbo].[LITACapstoneDataset]
GROUP BY Product;

---5 Monthly sales totals for the current year---
SELECT MONTH (OrderDate) AS Month,SUM(Revenue) AS Total_sales
FROM [dbo].[LITACapstoneDataset]
WHERE YEAR(OrderDate) = YEAR (GETDATE())
GROUP BY MONTH (OrderDate)
ORDER BY MONTH;


---- 6 Top 5 customers by Total purchase amount---
SELECT TOP 5 Customer_Id, SUM (Revenue) AS Total_purchase_amount
FROM [dbo].[LITACapstoneDataset]
GROUP BY Customer_Id
ORDER BY Total_purchase_amount DESC;

--- 7 calculate the percentage of total sales contributed by each region---
 
SELECT Region, SUM(Revenue) AS Region_sales,
  COUNT(Revenue) * 100.0 /Sum (COUNT(Revenue))
  OVER() AS Sales_percentage
FROM [dbo].[LITACapstoneDataset]
GROUP BY Region

SELECT * FROM [dbo].[LITACapstoneDataset]
---8 identify products with no sales in the last quarter---

SELECT Product
FROM [dbo].[LITACapstoneDataset]
GROUP BY Product
HAVING MAX(OrderDate) < DATEADD(QUARTER,-1,GETDATE());
```

### Data visualization

Interactive dashboards and visual representations were created to make the insights found in excel, SQL accessible and engaging such as overview of all sales,top performing product and the regional breakdowns using PowerBI.The visuals shows the highest selling product which is 'shoe',the region with the highest revenue which is 'south'.The 'Year','Quarter','Month' ,'Day' and 'Region' was filtered out in order to be able to know the actual revenue based on any of the filtered criteria.


<img width="612" alt="capstone sales" src="https://github.com/user-attachments/assets/c65fb2d2-cdd0-4a8f-824e-f8fb60d7e06c">

### Conclusion

This project not only showcased the power of data analysis but also emphasized the importance of translating data into compelling stories.By leveraging data insights,we are able to make informed decisions that propels us towards our objectives and ensure sustained success.
