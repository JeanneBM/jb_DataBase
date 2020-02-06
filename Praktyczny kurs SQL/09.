USE AdventureWorksLT2012
GO

SELECT [FirstName]
FROM [SalesLT].[Customer];
GO

SELECT [Title], COUNT(*)
FROM [SalesLT].[Customer]
GROUP BY [Title]
ORDER BY COUNT(*);
GO

SELECT [SalesOrderID], [LineTotal]
FROM [SalesLT].[SalesOrderDetail];

SELECT [SalesOrderID], [LineTotal]
FROM [SalesLT].[SalesOrderDetail]
ORDER BY [LineTotal] DESC;
GO

SELECT [SalesOrderID]
FROM [SalesLT].[SalesOrderDetail]
ORDER BY [LineTotal] DESC;

SELECT [SalesOrderID], [LineTotal]
FROM [SalesLT].[SalesOrderDetail]
ORDER BY [LineTotal] DESC;
GO

SELECT *
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID = 836;


SELECT [SalesOrderID], ProductID
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID = 836;
GO

SELECT *
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID = 997;
GO

SELECT *
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID <> 999;
GO

SELECT [SalesOrderID], ProductID
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID = 997;

SELECT [SalesOrderID], ProductID
FROM [SalesLT].[SalesOrderDetail]
WHERE ProductID+0  = 997;
GO

SELECT *
FROM [SalesLT].[Customer]
WHERE [EmailAddress] = 'keith0@adventure-works.com';

SELECT *
FROM [SalesLT].[Customer]
WHERE LOWER([EmailAddress]) = 'keith0@adventure-works.com';
GO

SELECT [ProductID], COUNT(*)
FROM [SalesLT].[SalesOrderDetail]
GROUP BY [ProductID];

SELECT [ProductID], COUNT(*)
FROM [SalesLT].[SalesOrderDetail] WITH (INDEX(0))
GROUP BY [ProductID];
GO

/*

*/
SELECT [Name]
FROM [SalesLT].[Product]
UNION 
SELECT [Name]
FROM [SalesLT].[ProductCategory];

SELECT [Name]
FROM [SalesLT].[Product]
UNION ALL
SELECT [Name]
FROM [SalesLT].[ProductCategory]
GO

SELECT [SalesOrderID]
FROM [SalesLT].[SalesOrderDetail]
WHERE [UnitPrice]*.77 > 900;


SELECT [SalesOrderID]
FROM [SalesLT].[SalesOrderDetail]
WHERE [UnitPrice] > 900 / 0.77
GO

SELECT [DueDate], [SalesOrderID], [TotalDue],
	LAG([TotalDue]) OVER (PARTITION BY [DueDate] ORDER BY [DueDate]) as PreviusTotalDue
FROM [SalesLT].[SalesOrderHeader]
ORDER BY [DueDate];


