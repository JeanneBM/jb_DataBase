USE AdventureWorksLT2012
GO

INSERT INTO [dbo].[ErrorLog]
VALUES (GETDATE(),'MARCIN');
GO

INSERT INTO FOO ([NAME])
VALUES ('Marcin');
GO

INSERT INTO FOO ([AGE], [NAME])
VALUES(5, 'Bob');
GO

SELECT * 
FROM FOO;
GO

INSERT INTO [SalesLT].[ProductCategory] ([Name])
VALUES ('New Category');
GO

SELECT [ProductCategoryID], [ParentProductCategoryID], [Name]
FROM [SalesLT].[ProductCategory]
WHERE [Name] = 'New Category';
GO

INSERT INTO [SalesLT].[ProductCategory] ([ProductCategoryID], [Name])
VALUES (1234, 'Newest Category');
GO

INSERT INTO [SalesLT].[ProductCategory] ([Name])
VALUES ('Newest Category');
GO

SELECT *
FROM [SalesLT].[ProductCategory]
WHERE [Name] = 'Newest Category';
GO


INSERT INTO [SalesLT].[ProductCategory] ([Name],[ModifiedDate])
VALUES ('Spices', '2014-10-10');
GO

SELECT [Name],[ModifiedDate]
FROM [SalesLT].[ProductCategory]
WHERE [Name] = 'Spices';
GO

INSERT INTO [SalesLT].[ProductCategory] ([Name],[rowguid],[ModifiedDate])
VALUES ('Herbs', DEFAULT,DEFAULT);
GO

SELECT [Name],[rowguid], [ModifiedDate]
FROM [SalesLT].[ProductCategory]
WHERE [Name] = 'Herbs';
GO

INSERT INTO [dbo].[ErrorLog] ([UserName],[ErrorNumber], [ErrorMessage])
VALUES ('Marcin',50000,'Test message');
GO

SELECT *
FROM [dbo].[ErrorLog]
WHERE [ErrorNumber] = 50000;
GO

INSERT INTO [dbo].[ErrorLog] 
	([ErrorTime],[UserName],[ErrorNumber], [ErrorSeverity],[ErrorState],[ErrorProcedure],[ErrorLine],[ErrorMessage])
VALUES (DEFAULT,'Marcin',50001,NULL,NULL,NULL,NULL,'Test message');
GO

INSERT INTO [SalesLT].[ProductCategory] ([Name])
VALUES (NULL);
GO

INSERT INTO FOO ([NAME], [AGE])
VALUES ('Bob', 5), ('Mary', 6);
GO

SELECT *
INTO #PROD
FROM [SalesLT].[Product]
WHERE ListPrice>100;
GO

SELECT [ProductID], [Name], [ListPrice]*2 AS DoubledPrice
INTO #OverPriced
FROM [SalesLT].[Product]

SELECT *
INTO EmptyTable
FROM [SalesLT].[Product]
WHERE 1=0;
GO

INSERT INTO EmptyTable
SELECT *
FROM [SalesLT].[Product];
GO

INSERT INTO EmptyTable ([Name])
VALUES (NULL);
GO

INSERT INTO EmptyTable
           ([Name]
           ,[ProductNumber]
           ,[Color]
           ,[StandardCost]
           ,[ListPrice]
           ,[Size]
           ,[Weight]
           ,[ProductCategoryID]
           ,[ProductModelID]
           ,[SellStartDate]
           ,[SellEndDate]
           ,[DiscontinuedDate]
           ,[ThumbNailPhoto]
           ,[ThumbnailPhotoFileName]
           ,[rowguid]
           ,[ModifiedDate])
SELECT [Name]
           ,[ProductNumber]
           ,[Color]
           ,[StandardCost]
           ,[ListPrice]
           ,[Size]
           ,[Weight]
           ,[ProductCategoryID]
           ,[ProductModelID]
           ,[SellStartDate]
           ,[SellEndDate]
           ,[DiscontinuedDate]
           ,[ThumbNailPhoto]
           ,[ThumbnailPhotoFileName]
           ,[rowguid]
           ,[ModifiedDate]
FROM [SalesLT].[Product];		      
GO

INSERT INTO Napoje ([Nazwa produktu], [Kod produktu], Cena)
SELECT [Nazwa produktu],[Kod produktu], [Cena katalogowa]
FROM dbo.Produkty AS P
WHERE NOT EXISTS
  (SELECT *
  FROM Napoje AS O
  WHERE O.[Kod produktu] = P.[Kod produktu]);


INSERT INTO #PROD 
			([Name]
           ,[ProductNumber]
           ,[Color]
           ,[StandardCost]
           ,[ListPrice]
           ,[Size]
           ,[Weight]
           ,[ProductCategoryID]
           ,[ProductModelID]
           ,[SellStartDate]
		   ,[rowguid]
           ,[ModifiedDate])
SELECT [Name]
       ,[ProductNumber]
       ,[Color]
       ,[StandardCost]
       ,[ListPrice]
       ,[Size]
       ,[Weight]
       ,[ProductCategoryID]
       ,[ProductModelID]
       ,[SellStartDate]
	   ,[rowguid]
       ,[ModifiedDate]
FROM [SalesLT].[Product] AS P
WHERE NOT EXISTS
  (SELECT *
  FROM #PROD AS N
  WHERE P.ProductNumber = N.ProductNumber);
GO

DELETE FROM [dbo].[EmptyTable];
GO

DELETE FROM #PROD
WHERE [SellEndDate] IS NULL;

DELETE FROM [SalesLT].[Product];
GO

DELETE P
FROM [SalesLT].[Product] AS P 
LEFT OUTER JOIN [SalesLT].[ProductCategory] AS C 
ON P.ProductCategoryID = C.ProductCategoryID
WHERE P.ProductCategoryID IS NULL;
GO

INSERT INTO #PROD 
			([Name]
           ,[ProductNumber]
           ,[Color]
           ,[StandardCost]
           ,[ListPrice]
           ,[Size]
           ,[Weight]
           ,[ProductCategoryID]
           ,[ProductModelID]
           ,[SellStartDate]
		   ,[rowguid]
           ,[ModifiedDate])
SELECT [Name]
       ,[ProductNumber]
       ,[Color]
       ,[StandardCost]
       ,[ListPrice]
       ,[Size]
       ,[Weight]
       ,[ProductCategoryID]
       ,[ProductModelID]
       ,[SellStartDate]
	   ,[rowguid]
       ,[ModifiedDate]
FROM [SalesLT].[Product] AS P
GO

WITH Duplikaty AS
(SELECT *, ROW_NUMBER() OVER(PARTITION BY [ProductNumber] ORDER BY (SELECT 1)) AS Nr
FROM #PROD)
SELECT [ProductNumber] FROM Duplikaty
WHERE Nr>1;
GO


WITH Duplikaty AS
(SELECT *, ROW_NUMBER() OVER(PARTITION BY [ProductNumber] ORDER BY (SELECT 1)) AS Nr
FROM #PROD)
DELETE FROM Duplikaty
WHERE Nr>1;
GO

TRUNCATE TABLE #PROD;
GO

UPDATE Foo
SET [AGE]=18;
GO
 
 commit
UPDATE [SalesLT].[Customer]
SET [LastName] = 'Nowak'
WHERE [CustomerID]=1;
GO

UPDATE Foo
SET [AGE]=18, [NAME] = 'Tom'
WHERE [NAME] like 'Bo%';
GO

UPDATE [SalesLT].[Product]
SET [ListPrice] = [ListPrice]-[ListPrice]*0.1
WHERE [SellEndDate] IS NOT NULL;
GO

UPDATE [SalesLT].[Product]
SET [ListPrice] /= 2
WHERE [SellEndDate] IS NOT NULL;
GO

SELECT [FirstName], [LastName]
INTO Tab
FROM [SalesLT].[Customer];

SELECT *
FROM Tab;

UPDATE Tab
SET [FirstName] = [LastName],
	[LastName] = [FirstName];
GO

SELECT *
FROM Tab;
GO

UPDATE P
SET [StandardCost] *=0.85
FROM [SalesLT].[Product] AS P
JOIN [SalesLT].[SalesOrderDetail] AS D
	ON P.ProductID=D.ProductID
WHERE D.OrderQty>10;
GO

UPDATE P
SET P.[ModifiedDate] = D.[ModifiedDate]
FROM [SalesLT].[Product] AS P
JOIN [SalesLT].[SalesOrderDetail] AS D
	ON P.ProductID=D.ProductID
WHERE D.[SalesOrderID] BETWEEN 71500 AND 72000;
GO

CREATE TABLE #O1soby (ID int identity(1,1), Imie varchar(100));
GO

MERGE INTO #Osoby
USING (Values ('Danuta',1),('Marcin',2)) Znajomi(Imie,Numer)
ON #Osoby.ID = Znajomi.Numer
WHEN NOT MATCHED THEN
INSERT (imie) values (Znajomi.Imie);
GO

SELECT * FROM #Osoby;

MERGE INTO #Osoby
USING (Values ('Krzys',3),('Michal',2)) Znajomi(Imie,Numer)
ON #Osoby.ID = Znajomi.Numer
WHEN MATCHED THEN 
  UPDATE SET #Osoby.Imie = Znajomi.Imie
WHEN NOT MATCHED THEN
  INSERT (imie) values (Znajomi.Imie);
GO

SELECT * FROM #Osoby;
GO

MERGE INTO #Osoby
USING (Values ('Danuta',1),('Marcin',2)) Znajomi(Imie,Numer)
ON #Osoby.ID = Znajomi.Numer
WHEN MATCHED THEN 
UPDATE SET #Osoby.Imie = Znajomi.Imie
WHEN NOT MATCHED THEN
INSERT (imie) values (Znajomi.Imie)
WHEN NOT MATCHED BY SOURCE THEN
DELETE;
GO

SELECT * FROM #Osoby;
GO
