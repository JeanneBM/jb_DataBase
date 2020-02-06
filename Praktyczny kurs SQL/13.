USE AdventureWorksLT2012
GO

SELECT [ProductID], [ProductNumber], [ListPrice]
FROM [SalesLT].[Product]
WHERE [SellEndDate] IS NULL;
GO

CREATE VIEW [SalesLT].[CurrrentProduct]
AS
SELECT [ProductID], [ProductNumber], [ListPrice]
FROM [SalesLT].[Product]
WHERE [SellEndDate] IS NULL;
GO

SELECT TOP 5 *
FROM [SalesLT].[CurrrentProduct]
ORDER BY [ListPrice] DESC;
GO

CREATE VIEW dbo.OrderedProducts 
AS
SELECT TOP 100 PERCENT C.[Name] AS Cat, P.[Name] AS Prod
FROM [SalesLT].[ProductCategory] AS C
JOIN [SalesLT].[Product] AS P
ON C.ProductCategoryID = P.ProductCategoryID
ORDER BY C.[Name];
GO

SELECT *
FROM OrderedProducts;
GO

SELECT *
FROM OrderedProducts
ORDER BY Cat;
GO

ALTER VIEW dbo.OrderedProducts 
AS
SELECT  C.[Name] AS Cat, P.[Name] AS Prod, P.ListPrice
FROM [SalesLT].[ProductCategory] AS C
JOIN [SalesLT].[Product] AS P
ON C.ProductCategoryID = P.ProductCategoryID;
GO

SELECT * 
FROM dbo.OrderedProducts 

SELECT  C.[Name] AS Cat, P.[Name] AS Prod, P.ListPrice
FROM [SalesLT].[ProductCategory] AS C
JOIN [SalesLT].[Product] AS P
ON C.ProductCategoryID = P.ProductCategoryID;
GO

CREATE VIEW [SalesLT].[vOrders]
AS
SELECT P.ProductNumber, OD.LineTotal
FROM [SalesLT].[SalesOrderDetail] AS OD
JOIN [SalesLT].[CurrrentProduct] AS P
ON P.ProductID = OD.ProductID;
GO

SELECT * 
FROM [SalesLT].[vOrders];
GO

CREATE VIEW [SalesLT].[DailySales] (OrderDate, Clients, Orders, AvgDue)
AS
SELECT [OrderDate], COUNT(DISTINCT [CustomerID]), 
	COUNT (DISTINCT [SalesOrderID]), AVG([TotalDue])
FROM [SalesLT].[SalesOrderHeader]
GROUP BY [OrderDate];
GO

SELECT *
FROM [SalesLT].[DailySales]
WHERE AvgDue>10
AND Clients>2;
GO

CREATE VIEW [SalesLT].[Bikes]
AS
WITH CategoryCTE([ParentProductCategoryID], [ProductCategoryID], [Name]) AS 
(
	SELECT [ParentProductCategoryID], [ProductCategoryID], [Name]
	FROM SalesLT.ProductCategory
	WHERE ProductCategoryID =1
UNION ALL
	SELECT C.[ParentProductCategoryID], C.[ProductCategoryID], C.[Name]
	FROM SalesLT.ProductCategory AS C
	INNER JOIN CategoryCTE AS BC ON BC.ProductCategoryID = C.ParentProductCategoryID
)

SELECT CCTE.[Name] as [ProductCategoryName], P.Name, P.Color
FROM CategoryCTE AS CCTE
JOIN [SalesLT].[Product] AS P
ON CCTE.ProductCategoryID=p.ProductCategoryID;
GO

UPDATE [SalesLT].[Bikes]
SET Color = 'Dark'
WHERE Name = 'Road-750 Black, 44';
GO

SELECT * 
FROM [SalesLT].[Bikes];
GO

CREATE VIEW vClients
AS
SELECT [CustomerID], [FirstName], [LastName]
FROM [dbo].[Panie]
WHERE FirstName LIKE 'D%';
GO

SELECT *
FROM vClients;
GO

INSERT INTO vClients ([FirstName],[LastName])
VALUES ('Anna','Nowak');
GO

SELECT *
FROM vClients;
GO

UPDATE vClients
SET [FirstName] = 'Rosmarie'
WHERE CustomerID = 334;
GO

SELECT *
FROM vClients;
GO

ALTER VIEW vClients
AS
SELECT [CustomerID], [FirstName], [LastName]
FROM [dbo].[Panie]
WHERE FirstName LIKE 'D%'
WITH CHECK OPTION;
GO

UPDATE vClients
SET [FirstName] = 'Rosmarie'
WHERE CustomerID = 84;
GO

CREATE INDEX IX_SalesOrderDetailLineTotal
ON [SalesLT].[SalesOrderDetail] ([LineTotal]);
GO

SELECT *
FROM [SalesLT].[SalesOrderDetail]
WHERE [LineTotal]<50;
GO

SELECT *
FROM [SalesLT].[SalesOrderDetail]
WHERE [LineTotal]<50;

SELECT *
FROM [SalesLT].[SalesOrderDetail] WITH (INDEX ([IX_SalesOrderDetailLineTotal]))
WHERE [LineTotal]<50;
GO

DROP INDEX [IX_SalesOrderDetailLineTotal]
ON [SalesLT].[SalesOrderDetail];
GO

CREATE INDEX IX_SalesOrderDetailComposite
ON [SalesLT].[SalesOrderDetail] ([LineTotal], [OrderQty]);
GO

SELECT [SalesOrderID], [LineTotal], [OrderQty]
FROM [SalesLT].[SalesOrderDetail] 
WHERE [LineTotal]<50;

SELECT [SalesOrderID], [LineTotal], [OrderQty]
FROM [SalesLT].[SalesOrderDetail] WITH (INDEX (1))
WHERE [LineTotal]<50;
GO

CREATE UNIQUE INDEX IX_Products
ON [SalesLT].[Product] ([ProductNumber], [StandardCost], [SellStartDate]);
GO

CREATE INDEX IX_CurrentProducts
ON [SalesLT].[Product] ([ProductNumber], [StandardCost], [SellStartDate], [SellEndDate])
WHERE [SellEndDate] IS NOT NULL;
GO

ALTER INDEX ALL
ON [SalesLT].[Product]
REBUILD;
GO

ALTER INDEX IX_CurrentProducts
ON [SalesLT].[Product]
REBUILD;

ALTER INDEX IX_CurrentProducts
ON [SalesLT].[Product]
REORGANIZE;


