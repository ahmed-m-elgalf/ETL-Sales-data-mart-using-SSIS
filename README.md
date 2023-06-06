# ETL Sales data mart using SSIS



### Overview
The objective is to convert adventureworks ERD to sales data warehouse for analysis and reporting and answer some key business questions for example :
* What is our sales trend over time ?
* How number of orders change ?
* Which products /  categories generate best sales  ?
* What the total number of our customers and Who are our loyal customers ?
* How our customers are segmented based on their location ?

and many other questions to improve business performance and track import business KPIs
so for each dimension I extracted required columns from different tables and performed different transformation

#### Dim customer
Data collected from required tables
I implemented slowly changing dimension for dim customers and used customerID as business key to track changes on this dimension
I used Type 2 SCD for phone number to track history of changes of phone numbers for each customer using start time , end time and is current columns
I used type 1 SCD to update address line , city , customer name
Used surrogate key to as identity column for dim customer



#### Dim product
I used Type 2 SCD for reorder point  to track history of changes of reorder point using start time , end time and is current columns

I used type 1 SCD  to update category , color , description , model name , product name ,  standard cost and subcategory
Used surrogate key to as identity column for dim customer

#### Factsales
To populate fact sales table  I used sales orderID  table then matched with each dimension to get dim key using lookup component then loaded the final data into Fact table



![Screenshot: ](img/1.png )

