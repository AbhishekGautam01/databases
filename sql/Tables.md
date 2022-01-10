# CTE, Temp Table, Table Variable 

## CTE - Common Table Expression 
* Introduced in SQL Server 2005 
* **Temporary result set** and typically a result of complex sub query 
* Lifetime is limited to current query .
* Define using **WITH** statement. 
* CTE always beings with a ; **semicolon** 
* It is used to create Recursive query or storing result of complex sub query. 

```
;With CTE1(Address, Name, Age)--Column names for CTE, which are optional
AS
(
SELECT Addr.Address, Emp.Name, Emp.Age from Address Addr
INNER JOIN EMP Emp ON Emp.EID = Addr.EID
)
SELECT * FROM CTE1 --Using CTE 
```

## Temporary Table 
* Created at runtime and we can perform any action on these tables as we do on normal table 
* It exists in tempdb 
* Automatically deleted when the created session is closed. 
* The name of the table start with Single # 

```
CREATE TABLE #LocalTemp
(
 UserID int,
 Name varchar(50), 
 Address varchar(150)
)
GO
insert into #LocalTemp values ( 1, 'Shailendra','Noida');
GO
Select * from #LocalTemp

```

### Global Temporary Tables 
* It is available to all SQL Server sessions/Connections i.e. all end users. 
* They are deleted when all connection to SQL Server close. 
* The name starts with ## symbol 

```
CREATE TABLE ##GlobalTemp
(
 UserID int,
 Name varchar(50), 
 Address varchar(150)
)
GO
insert into ##GlobalTemp values ( 1, 'Shailendra','Noida');
GO
Select * from ##GlobalTemp
```

## Table Variable 
* Act as a variable and exists for a batch of query execution
* It gets dropped when we come out of that batch 
* Allows us to create a PK 

```
GO
 DECLARE @TProduct TABLE
 (
 SNo INT IDENTITY(1,1),
 ProductID INT,
 Qty INT
 ) 
 --Insert data to Table variable @Product 
 INSERT INTO @TProduct(ProductID,Qty)
 SELECT DISTINCT ProductID, Qty FROM ProductsSales ORDER BY ProductID ASC 
 --Select data
 Select * from @TProduct
 
 --Next batch
 GO
 Select * from @TProduct --gives error in next batch
```