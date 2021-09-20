# SQL Challenge



## a. How many orders were shipped by Speedy Express in total?



`SELECT count(*) FROM Orders o
	JOIN SHIPPERS s
	ON s.shipperid = o.shipperid
	WHERE o.shipperid = 1` 



*Answer*: 54



## b. What is the last name of the employee with the most orders?

`SELECT COUNT(*) AS OrderCount, o.EmployeeID , e.lastname, e.firstname
	FROM Orders o
    JOIN EMPLOYEES e
    	ON o.EmployeeID = e.EmployeeID
	GROUP BY o.EmployeeID 
    ORDER BY OrderCount DESC
    LIMIT 1`



*Answer*: Peacock



## c. What product was ordered the most by customers in Germany?



`SELECT p.ProductName, c.Country, SUM(od.Quantity) AS Total
	FROM Orders o
    JOIN Customers c
    	ON o.CustomerID = c.CustomerID
	JOIN OrderDetails od
    	ON od.OrderID = o.OrderID
	JOIN Products p
    	ON p.ProductID = od.ProductID
    WHERE c.Country = "Germany"
    GROUP BY p.ProductName
    ORDER BY Total DESC
    LIMIT 1`



*Answer*: Boston Crab Meat