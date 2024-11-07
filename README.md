# LITA_Capstone_Project
This is where I will be documenting the progress of my final project analysis throughout the Incubator Hub Data Analysis training program.

### Project Outline.
- [Project Title](#project-title)


### Project Title: Sales Data and Customer Data Analysis.

### Project Overview:

This project is aimed at analysing the Sales and Customer data to uncover key trends and actionable insights. The goal is to evaluate how the company is fairing now in terms of their sales trend, Customer retention and to provide data-driven recommendations to improve the company’s sales performance and Customer's retention in the coming years.

### Data Source: 
The primary data used here is an open source data sub file downloaded from the LITA_Capstone_Data. csv file which was downloaded from the Incubator Hub Learning Management System. It consists of the Sales Data file and Customer Data File.

### Tools Used
- Microsoft Excel [Download here](https://www.microsoft.com)
 1. For Data Cleaning.
 2. For Analysis.
 3. For Visualization.

- Structured Query Language(SQL)
 1. For Querying the dataset.
 2. Cleaning the Dataset.

- PowerBI [Download here](https://www.microsoft.com)
 1. For portfolio building.


### Exploratory Data Analysis

This data is analysed to answer the following Sales trend and revenue generating questions:

- Which product generated the most revenue in terms of sales in 2023 and 2024
- The total revenue generated by the products across various regions in 2023 and 2024
- The average unit of product sold in the various regions.
- The product with the top sales.

  ### Sales Data Analysis

  The data set was cleaned using Microsoft Excel and the following functions were used to calculate Total Revenue, Average Revenue of the products,
  
```Excel

   Total Revenue : =(Unit Price * Quantity) [Enter]
  
  Average Revenue: =AVERAGEIF( Range , criteria,[average range]) [Enter]
```


The pivot table was used to summarize the sales data to discover some trends. An example of such is the total revenue generated by each of the products over the two years ( 2023 and 2024)

  
![image](https://github.com/user-attachments/assets/b43abc2b-8dbe-471c-b666-93113f614074)


The Structured query language used to answer the following questions for more insights on the Sales data include the following:

1.  The total sales for each product category.
  ```sql
  SELECT * Product, SUM(Quantity * UnitPrice) AS TotalSales
   FROM SalesData
   GROUP BY Product
   ORDER BY TotalSales DESC  
```

2.  The number of sales transactions in each region.
```sql
  SELECT Region, COUNT(OrderID) AS TransactionCount
  FROM SalesData
  GROUP BY Region;
```

3. The highest-selling product by total sales value.
  ```sql
  SELECT TOP 1 Product, SUM(Quantity * UnitPrice) AS TotalSales
  FROM SalesData
  GROUP BY Product
  ORDER BY TotalSales DESC;
  ```

 4. The total revenue per product.
  ```sql
  SELECT Product, SUM(Quantity * UnitPrice) AS TotalRevenue
  FROM SalesData
  GROUP BY Product
  ORDER BY TotalRevenue DESC;
  ```
  5. The monthly sales totals for the current year.
```sql

 SELECT MONTH(OrderDate) AS SaleMonth, SUM(Quantity * UnitPrice) AS MonthlySales
 FROM SalesData
 WHERE YEAR(OrderDate) = YEAR(GETDATE()) 
 GROUP BY MONTH(OrderDate)
 ORDER BY SaleMonth;
```

6. The top 5 customers by total purchase amount.
   ```sql
   SELECT CustomerId, SUM(Quantity * UnitPrice) AS TotalPurchase
   FROM SalesData
   GROUP BY CustomerId
   ORDER BY TotalPurchase DESC
   OFFSET 0 ROWS FETCH NEXT 5 ROWS ONLY;
   ```
and so on.
  
### Key Insights Gotten from the Sales Data

- It was noted after the analysis that the Total Revenue generated by the company in the space of two years(2023 and 2024) is 10,587,500.
- The region with the highest revenue was the south for the two years with a revenue of 2,425,000 in 2023 and 2,250,000 in 2024 although a downturn in revenue was reported.The region with the lowest return was the west in 2023 and the east in 2024 with 437,500 and 462500 respectively.
- Our top sales product for the two years is Shoes for the with a total revenue of 1,400,000 in 2023 and 1,687,500 in 2024.
- In 2023, the business generated revenue for all the quarters with the highest revenue generated in the first quarter. While in 2024, the business generated revenue in the first three quarters and none in the last quarter, the highest revenue generated also was in the first quarter.
-  The average revenue on products sold in the various regions are East (196), West (121), North (156), South (374) 

### Recommendation 
- The head of the operation and sales department of the northen and western regions are to be asked for what they did differently to boost their sales from 725000 to 1225000 and 437,500 to 1,075,000 respectively. This should be encouraged to ensure a continued increase in sales provided every other factors are kept constant. Staffs of those region can also be rewarded for a job well done to boost production capacity.
- Critical investigation is to be carried out on the eastern region to understand the reason behind the crash in sales between 2023 and 2024 from 1,987,500 to 462,500.
- Across every region, investigations have to be conducted to ascertain why sales was not possible in the fourth quarter of 2024 for all products.


  

