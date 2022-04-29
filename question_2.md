# Part 1

SELECT COUNT(O.OrderID) AS NumOfOrders, S.ShipperName AS ShipperName
FROM Orders AS O, Shippers AS S
WHERE O.ShipperID = S.ShipperID
AND S.ShipperName = "Speedy Express"

# Part 2

SELECT E.LastName AS LastName, O.EmployeeID AS EmployeeID, COUNT(O.OrderID) AS NumOfOrders
FROM Orders as O, Employees AS E
WHERE O.EmployeeID = E.EmployeeID
GROUP BY O.EmployeeID
ORDER BY COUNT(O.OrderID) DESC
LIMIT 1

# Part 3

SELECT P.ProductName AS ProductName, COUNT(P.ProductID) AS ProductID
FROM Products AS P, OrderDetails AS OD, Orders AS O, Customers AS C
WHERE P.ProductID = OD.ProductID AND
	  OD.OrderID = O.OrderID AND
      O.CustomerID = C.CustomerID AND
      C.Country = "Germany"
GROUP BY P.ProductID
ORDER BY COUNT(P.ProductID) DESC
LIMIT 1