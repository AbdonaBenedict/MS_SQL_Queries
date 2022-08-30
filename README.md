# MS_SQL_Queries
Basic Queries of Microsoft SQL Server

Use AdventureWorks2019;





select 
* from HumanResources.Shift;

select ShiftID,Name
from HumanResources.Shift;

select
* from HumanResources.Department;

select DepartmentID,Name
 from HumanResources.Department where GroupName = 'Manufacturing';

 select DepartmentID,Name
 from HumanResources.Department where DepartmentID > 20;

 select *
 from HumanResources.Department;

 select *
 from Purchasing.PurchaseOrderHeader;

 select SubTotal,TaxAmt 
 from Purchasing.PurchaseOrderHeader;

 select SubTotal, TaxAmt, SubTotal+TaxAmt as SubTotalWithTaxAmt
 from Purchasing.PurchaseOrderHeader;

 select SubTotal, TaxAmt, SubTotal+TaxAmt as SubTotalWithTaxAmt
 from Purchasing.PurchaseOrderHeader where TaxAmt > 100;

 select *
 from HumanResources.vEmployee

 select FirstName, MiddleName, LastName 
 from HumanResources.vEmployee;

 select FirstName, MiddleName, LastName, FirstName + ' ' + MiddleName +' ' + LastName as FullName 
 from HumanResources.vEmployee;


 select FirstName, MiddleName, LastName, FirstName + ' ' + MiddleName +' ' + LastName as FullName 
 from HumanResources.vEmployee 
 where MiddleName IS NULL;

 select FirstName, MiddleName, LastName, FirstName + ' ' + MiddleName +' ' + LastName as FullName 
 from HumanResources.vEmployee 
 where MiddleName IS NOT NULL;

 select *
 from Person.StateProvince;

 select StateProvinceID, StateProvinceCode, CountryRegionCode
 from Person.StateProvince 
 where StateProvinceCode = 'AB' AND CountryRegionCode = 'CA';

 select StateProvinceID, StateProvinceCode, CountryRegionCode
 from Person.StateProvince 
 where StateProvinceID IN (5,10,15);

 select StateProvinceID, StateProvinceCode, CountryRegionCode
 from Person.StateProvince 
 where StateProvinceID BETWEEN 1 AND 10;

 select StateProvinceID, StateProvinceCode, CountryRegionCode, Name
 from Person.StateProvince 
 where Name LIKE 'A%';

 select StateProvinceID, StateProvinceCode, CountryRegionCode, Name
 from Person.StateProvince 
 where Name LIKE '%o';

 select StateProvinceID, StateProvinceCode, CountryRegionCode, Name
 from Person.StateProvince 
 where Name LIKE 'A___';

 select StateProvinceID, StateProvinceCode, CountryRegionCode, Name
 from Person.StateProvince 
 where Name LIKE 'A%__%e';

 select City, PostalCode
 from Person.Address 
 ORDER BY City desc;

 select City, PostalCode
 from Person.Address 
 ORDER BY City;

 select SalesOrderID, UnitPrice
 from Sales.SalesOrderDetail;

 select SalesOrderID, SUM(UnitPrice) AS UnitPriceSum
 from Sales.SalesOrderDetail 
 GROUP BY SalesOrderID;

 select SalesOrderID, AVG(UnitPrice) AS UnitPriceSum
 from Sales.SalesOrderDetail 
 GROUP BY SalesOrderID;

 select SalesOrderID, COUNT(UnitPrice) AS UnitPriceSum
 from Sales.SalesOrderDetail 
 GROUP BY SalesOrderID;

 select SalesOrderID, MAX(UnitPrice) AS UnitPriceSum
 from Sales.SalesOrderDetail 
 GROUP BY SalesOrderID;

 select SalesOrderID, MIN(UnitPrice) AS UnitPriceSum
 from Sales.SalesOrderDetail 
 GROUP BY SalesOrderID;

 select FirstName, MiddleName, LastName 
 from HumanResources.vEmployee;

 select FirstName, MiddleName, LastName, CONCAT (FirstName,' ', MiddleName,' ',LastName) AS FullName
 from HumanResources.vEmployee;

 select FirstName, LEN(FirstName)
 from HumanResources.vEmployee;

 select FirstName, LEFT(FirstName,2) AS FIRSTNAMELEFTEXTRACT
 from HumanResources.vEmployee;

 select FirstName, RIGHT(FirstName,2) AS FIRSTNAMERIGHTEXTRACT
 from HumanResources.vEmployee;

 select FirstName, SUBSTRING(FirstName,3,2) AS FIRSTNAMESUBSTRING
 from HumanResources.vEmployee;

 select OrderDate
 from Sales.SalesOrderHeader;

 select DAY(OrderDate)
 from Sales.SalesOrderHeader;

 select MONTH(OrderDate)
 from Sales.SalesOrderHeader;

 select YEAR(OrderDate)
 from Sales.SalesOrderHeader;

 select CURRENT_TIMESTAMP;

 select SalesOrderID, sum(TaxAmt) AS TaxAmountTotal
 from Sales.SalesOrderHeader
 GROUP BY SalesOrderID
 HAVING SUM(TaxAmt) > 10000
 ORDER BY SalesOrderID DESC;

 --From->Where->Group By->Having->Select->Order by

 select PurchaseOrderID, EmployeeID
 from Purchasing.PurchaseOrderHeader;

 select PurchaseOrderID, PurchaseOrderDetailID
 from Purchasing.PurchaseOrderDetail;

 select PurchaseOrderID, EmployeeID 
 from Purchasing.PurchaseOrderHeader where PurchaseOrderID IN 
 (Select PurchaseOrderID from Purchasing.PurchaseOrderDetail where PurchaseOrderID > 50);

 select BusinessEntityID
 from HumanResources.Employee
 UNION 
 select BusinessEntityID
 from Person.Person
 UNION 
 select CustomerID
 from Sales.Customer;

 select BusinessEntityID
 from HumanResources.Employee
 UNION ALL 
 select BusinessEntityID
 from Person.Person
 UNION ALL
 select CustomerID
 from Sales.Customer;

 select pod.PurchaseOrderID, pod.PurchaseOrderDetailID, poh.EmployeeID
 from Purchasing.PurchaseOrderDetail pod
 INNER JOIN
 Purchasing.PurchaseOrderHeader poh
 ON pod.PurchaseOrderID = poh.PurchaseOrderID;

