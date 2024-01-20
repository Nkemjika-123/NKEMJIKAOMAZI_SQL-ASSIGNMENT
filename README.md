# NKEMJIKAOMAZI_SQL-ASSIGNMENT
#1 Branch with the highest sales revenue
select Branch, sum(Revenue) as Total_Revenue
from sales_table
group by Branch
order by Total_Revenue desc
limit 1;

#2	Pizza type with the most quantity sold
select Pizza_Sold,
sum(Quantity) as Total_Quantity,
max(Quantity) as Max_Quantity
from sales_table
group by Pizza_Sold
order by Total_Quantity desc;

#3	Average quantity of pizza sold per transaction for each branch
select Branch, avg(Quantity) as Avg_Quantity
from sales_table
group by Branch;


#4	Average unit price for each pizza type
select Pizza_Sold, avg(Price) as avg_unit_price
from sales_table 
group by Pizza_Sold;

#5	Sales performance of different branches in terms of the total sales and total quantity
select Branch, sum(Revenue) as Total_Revenue, sum(Quantity) as Total_Quantity
from sales_table
group by Branch;

#6	Sales performance of different pizza types in terms of the total sales and total quantity
select Pizza_Sold, sum(Revenue) as Total_Revenue, sum(Quantity) as Total_Quantity
from sales_table
group by Pizza_Sold;

#7	Retrieve the Branch and Pizza_sold and the sales revenue excluding transactions with a sales_Price 
#below 10000.
select Branch, Pizza_Sold, Revenue, sum(Price) as Total_Price
from sales_table
where Price >= 10000 
group by Branch, Pizza_Sold, Revenue;

#8	Calculate the total sales revenue for each Branch and Pizza_sold, and sort the results in descending order of revenue. 
#Exclude records where the Quantity sold is less than 5.
select Branch, Pizza_Sold, sum(Revenue) as Total_Revenue
from sales_table
where Quantity >= 5
group by Branch, Pizza_Sold
order by Total_Revenue desc;

#9	Calculate the total sales revenue for each Branch and Pizza_sold combination, considering only transactions with a Price between 2000 and 3000. 
#Sort the results by revenue in descending order.
select Branch, Pizza_Sold, Price, sum(Revenue) as Total_Revenue
from sales_table
where Price between 2000 and 3000
group by Branch, Pizza_Sold, Price
order by Total_Revenue desc;

#10.	Calculate the total sales revenue for each Branch and Pizza_sold combination, 
#and then sort the results by revenue in descending order. 
#For ties in revenue, sort by branch code in ascending order.
select Branch, Pizza_Sold, sum(Revenue) as Total_Revenue
from sales_table
group by Branch, Pizza_Sold
order by Total_Revenue desc, Branch asc;

#11	retrieve records of the branch,Pizza_Sold, Quantity, sales_price where the price is higher than 3000
select Branch, Pizza_Sold, Quantity, Price
from sales_table
where Price > 3000;

#12	get all record that the sales_price is greater than the 9000
select * from sales_table
where Price > 9000;

#13	retrieve records of the branch,Pizza_Sold, Quantity, sales_price 
#where the price is lower than the maximum price.
select Branch, Pizza_Sold, Quantity, Price
from sales_table
where Price < (select max(Price) from sales_table);


