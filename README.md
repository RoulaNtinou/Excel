# Sales Report Project


## Table of Contents

* [Problem Statement](#problem-statement)
* [Data Sourcing](#data-sourcing)
* [Data Presentation](#data-presentation)
* [Data Analysis](#data-analysis)
* [Insights](#insights)
- - - -
### Problem Statement

The purpose of this analysis is to provide a sales report per customer and country for the CEO of the company.

About:
* Transactions
* Profit
* Brands
* Products
* Regions
* Profit % change report
* Price Threshold Report
* Summary Report


- - - -
### Data Sourcing

The Dataset used for this analysis is a fictional dataset  and is available in the file above.

- - - -

### Data Presentation

> * The Dataset has 6 tables, with 10.281 customers, 24 stores in three countries and 1560 products.
> * The transactions were processed from 1/1/1997 until 31/12/1998.
> * Data Cleaning is done by importing the dataset with Power Query and Transform the data.


#### Diagram View

  > * After importing the data with Power Query, we Transform the data(checking: data types, headers names, text-columns adjustments,dates-column format)
  > and finally we Load the data to the Data Model.
  >
  > * Organize the tables in a relational database based on primary and foreign keys, by creating table relationships.
  >   
  > * Extract the Diagram View that follows.

 ![Diagram View](https://github.com/RoulaNtinou/Excel/blob/2e9fdf2b83f882ebcde8f1467f514701958ae909/DiagramView.png)

- - - -
### Data Analysis


1. >  The **transactions have increased more than 100% the second year and this is due to 11 stores bought** by the company at the beginning of 1998.
 
  
  ![Transactions per Year](https://github.com/RoulaNtinou/Excel/blob/313b0f92253cd9068bee5cbe1cda1a0cd5a38dc2/Transactions.png)


2. > The **new stores bought at the beginning of 1998**, are outside USA, and more specifically in Mexico and Canada.\
   > The increase of the profit depicts the acquisition of 11 stores in 1998.	


  ![Profit](https://github.com/RoulaNtinou/Excel/blob/7d964af56d42ffde0bc633d8eae04b90264ad6b0/Profit.png)
 


3. > The **top ten brands** based on the profit.

 ![Top10 Brands](https://github.com/RoulaNtinou/Excel/blob/7e79938b66b092370592b21d39e2feb06a1b302c/TopBrands.png)
  
  
 



4. > The **top 100 products** sorted by profit.\
   > The graph indicates a disparity between profitability and sales volume.	

![Products](https://github.com/RoulaNtinou/Excel/blob/7a51693037941635309d21b5619d695b4c437c02/Products.png)


5. > Stores per city, profit and year.\
   > The **cities are sorted according to the total profit for the two years**.
   > The only city that has two stores is Hidalgo
   
 ![Regions](https://github.com/RoulaNtinou/Excel/blob/29ab2c3ffd74b95b2fa1848fb7978a79e5c0adf9/CitiesProfit.png)


6. > Profit report for Month over Month percentage change.\
   > We can see the **seasonality of the profits and the huge increase at the beginning of 1998.**

![Profit % change report](https://github.com/RoulaNtinou/Excel/blob/f514b0a05db5585e2bcbce2ebcd2e131b2202012/ProfitChange.png)

7. > Price threshold for transactions and profit.\
   > This is a tool to **explore the source of profit based on the price of the products**
 ![Price Threshold Report](https://github.com/RoulaNtinou/Excel/blob/5d37a4343124cae0b24d032d8f0d25141b1e3efb/PriceThreshold.png)

8. > Summary Report\
   > **Increase of sales and profit and a profit margin about 60%.**
![Summary Report](https://github.com/RoulaNtinou/Excel/blob/988534207e5a02df28b4dac4212ae6d9d90be4de/SummaryTable.png)
   

- - - -

### Insights

* **Acquisition Impact**: The significant increase in transactions and profit in the second year is attributed to the acquisition of 11 stores at the beginning of 1998. This suggests that the acquisition strategy has been successful in driving growth and expanding market presence.

* **International Expansion**: The new stores acquired in 1998 are located outside the USA, specifically in Mexico and Canada. This indicates a strategic move towards international expansion, potentially tapping into new markets and diversifying the company's geographical footprint.
  
* **Profitability vs. Sales Volume**: The graph depicting a disparity between profitability and sales volume suggests that certain products or markets may be driving sales volume but not contributing significantly to overall profitability. This highlights the importance of analyzing profitability metrics alongside sales volume to make informed business decisions.
  
* **City-wise Profit Analysis**: Sorting cities according to total profit for the two years provides visibility into which cities are the most profitable markets for the company. This information can inform future expansion plans and resource allocation strategies.
  
* **Seasonality and Growth**: Seasonality patterns in profits, along with a notable increase at the beginning of 1998, indicate the impact of external factors or strategic initiatives on the company's financial performance. Understanding seasonality can help in planning inventory, staffing, and marketing activities effectively.
  
* **Price-based Profit Analysis**: The tool for exploring the source of profit based on product prices allows the company to identify the price thresholds that maximize transaction volume and profitability. This insight can inform pricing strategies and product assortment decisions.
  
* **Summary Report**: The overall increase in sales and profit, coupled with a healthy profit margin of about 60%, reflects positive financial performance and operational efficiency. It suggests that the company's strategic decisions, including acquisitions and international expansion, have been successful in driving growth and profitability.

