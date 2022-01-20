# Shopify-Data_Science_Inter_Challenge

Question 1:On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

1)Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
  Clearly we can see that the mean value 3145.128 is inaccurate since it is affeceted by a outlier value 704000.00
2)What metric would you report for this dataset?
  The interquartile range is the best measure of variability for skewed distributions or datasets with outliers. Because it's based on values that come from the middle half of the distribution, it's unlikely to be influenced by outliers, or We can also find median of data considering only the 50 percentage of data i.e considering only the values which lie between the first and the third quartile leaving out the values which are too high and too low.
3)What is its value?
  272.0

Question 2: For this question you’ll need to use SQL. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

1)How many orders were shipped by Speedy Express in total?
QUERY:-  select count(Orders.OrderID) from Orders join Shippers on Orders.ShipperID=Shippers.ShipperID where Shippers.ShipperName = 'Speedy Express';
Output:- 54

2)What is the last name of the employee with the most orders?
QUery:-  select e.LastName from Orders as o inner join Employees as e ON o.EmployeeID=e.EmployeeID GROUP BY e.LastName order by count(o.OrderID) desc limit 1;
Output:- Peacock
What product was ordered the most by customers in Germany?
Query:- select Products.ProductName from Orders INNER join Customers on Orders.CustomerID = Customers.CustomerID INNER join OrderDetails on Orders.OrderID = OrderDetails.OrderID           inner join Products on OrderDetails.ProductID = Products.ProductID where Customers.Country = 'Germany' group by Products.ProductName order by count(Products.ProductName)           desc limit 1;
Output: Gorgonzola Telino
