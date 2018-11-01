
1.** Which customers are from the UK **

``` SELECT * FROM [Customers] 
     WHERE Country = 'UK' ```
    
    
2. What is the name of the customer who has the most orders? (ANS:Ernst Handel)

``` SELECT OrderID, CustomerName, COUNT() AS OrderTimes 
    FROM Orders JOIN Customers ON Orders.CustomerID == Customers.CustomerID 
    GROUP BY CustomerName
    ORDER BY OrderTimes DESC``
    
    
3.Which supplier has the highest average product price? (ANS:Aux joyeux ecclésiastiques)


```SELECT SupplierName, AVG(Price) AS Average 
   FROM Suppliers JOIN Products ON Suppliers.SupplierID == Products.SupplierID
   GROUP BY SupplierName
   ORDER BY Average DESC ```
   
 
4.How many different countries are all the customers from? (ANS:21)

```SELECT COUNT (DISTINCT Country) FROM [Customers]```


5.What category appears in the most orders? (ANS:Dairy Products)

```SELECT CategoryName, COUNT(OrderID) AS OrderCount  FROM [OrderDetails] 
   JOIN Products ON OrderDetails.ProductID == Products.ProductID 
   JOIN Categories ON Products.CategoryID == Categories.CategoryID 
   GROUP BY CategoryName
   ORDER BY OrderCount DESC```
   
   
 6.What was the total cost for each order? 
 
 ```SELECT OrderID, SUM(Price) AS TotalCost FROM [OrderDetails] 
    JOIN Products ON OrderDetails.ProductID == Products.ProductID
    GROUP BY OrderID
    ORDER BY TotalCost DESC```
    
    
7.Which employee made the most sales (by total cost)?(ANS:Peacock Margaret)

```SELECT LastName,FirstName,SUM(Price*Quantity) AS TotalSales FROM Orders
   JOIN Employees ON Orders.EmployeeID ==Employees.EmployeeID
   JOIN OrderDetails ON Orders.OrderID == OrderDetails.OrderID
   JOIN Products On OrderDetails.ProductID == Products.ProductID
   GROUP BY Employees.EmployeeID
   ORDER BY TotalSales DESC ```
   
 8.Which employees have BS degrees?
 
 ```SELECT * FROM [Employees] WHERE Notes Like '%BS%'```
 
 
 9.Which supplier of three or more products has the highest average product price?(ANS:Tokyo Traders)
 
 ```SELECT SupplierName,COUNT(ProductID) AS NumberOfProducts, AVG(Price) AS AvgPrice FROM [Products]
    JOIN Suppliers ON Products.SupplierID == Suppliers.SupplierID
    GROUP BY SupplierName
    HAVING NumberOfProducts >= 3
    ORDER BY AvgPrice DESC```
 
 
