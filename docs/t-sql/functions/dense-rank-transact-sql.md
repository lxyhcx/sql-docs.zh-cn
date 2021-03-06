---
title: DENSE_RANK (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DENSE_RANK_TSQL
- DENSE_RANK
dev_langs:
- TSQL
helpviewer_keywords:
- row ranking [SQL Server]
- DENSE_RANK function
- tied rows [SQL Server]
- ranking rows
ms.assetid: 03871fc6-9592-4016-b0b2-ff543f132b20
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 54121ef549fb76639ec526b3128ffa8abfd7a849
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="denserank-transact-sql"></a>DENSE_RANK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回结果集分区中行的排名，在排名中没有任何间断。 行的排名等于所讨论行之前的所有排名数加一。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
DENSE_RANK ( ) OVER ( [ <partition_by_clause> ] < order_by_clause > )  
```  
  
## <a name="arguments"></a>参数  
 \<partition_by_clause>  
 将 [FROM](../../t-sql/queries/from-transact-sql.md) 子句生成的结果集划分为数个应用 DENSE_RANK 函数的分区。 有关 PARTITION BY 语法的信息，请参阅 [OVER 子句 (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)。  
  
 \<order_by_clause>  
 确定将 DENSE_RANK 函数应用于分区中各行的顺序。  
  
## <a name="return-types"></a>返回类型  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 如果有两个或多个行受同一个分区中排名的约束，则每个约束行将接收相同的排名。 例如，如果两位顶尖销售员具有相同的 SalesYTD 值，则他们将并列第一。 接下来 SalesYTD 最高的销售人员排名第二。 该排名等于该行之前的所有行数加一。 因此，DENSE_RANK 函数返回的数字没有间断，并且始终具有连续的排名。  
  
 整个查询所用的排序顺序确定了各行在结果中的显示顺序。 这说明排名第一的行可以不是分区中的第一行。  
  
 DENSE_RANK 具有不确定性。 有关详细信息，请参阅 [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)。  
  
## <a name="examples"></a>示例  
  
### <a name="a-ranking-rows-within-a-partition"></a>A. 对分区中的行进行排名  
 以下示例按照数量对指定清单位置的清单中的产品进行了排名。 结果集按 `LocationID` 分区并在逻辑上按 `Quantity` 排序。 注意，产品 494 和 495 具有相同的数量。 因为它们是关联的，所以两者均排名第一。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.ProductID, p.Name, i.LocationID, i.Quantity  
    ,DENSE_RANK() OVER   
    (PARTITION BY i.LocationID ORDER BY i.Quantity DESC) AS Rank  
FROM Production.ProductInventory AS i   
INNER JOIN Production.Product AS p   
    ON i.ProductID = p.ProductID  
WHERE i.LocationID BETWEEN 3 AND 4  
ORDER BY i.LocationID;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ProductID   Name                               LocationID Quantity Rank  
----------- ---------------------------------- ---------- -------- -----  
494         Paint - Silver                     3          49       1  
495         Paint - Blue                       3          49       1  
493         Paint - Red                        3          41       2  
496         Paint - Yellow                     3          30       3  
492         Paint - Black                      3          17       4  
495         Paint - Blue                       4          35       1  
496         Paint - Yellow                     4          25       2  
493         Paint - Red                        4          24       3  
492         Paint - Black                      4          14       4  
494         Paint - Silver                     4          12       5  
  
(10 row(s) affected)  
  
```  
  
### <a name="b-ranking-all-rows-in-a-result-set"></a>B. 对结果集中的所有行排名  
 下面的示例返回按薪金排名的前十名员工。 因为未指定 PARTITION BY 子句，所以，DENSE_RANK 函数应用于结果集中的所有行。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TOP(10) BusinessEntityID, Rate,   
       DENSE_RANK() OVER (ORDER BY Rate DESC) AS RankBySalary  
FROM HumanResources.EmployeePayHistory;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
BusinessEntityID Rate                  RankBySalary  
---------------- --------------------- --------------------  
1                125.50                1  
25               84.1346               2  
273              72.1154               3  
2                63.4615               4  
234              60.0962               5  
263              50.4808               6  
7                50.4808               6  
234              48.5577               7  
285              48.101                8  
274              48.101                8  
```  
  
## <a name="c-four-ranking-functions-used-in-the-same-query"></a>C. 用在同一查询中的四个排名函数  
 以下示例显示了用在同一查询中的四个排名函数。 有关函数特定的示例，请参阅每个排名函数。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,ROW_NUMBER() OVER (ORDER BY a.PostalCode) AS "Row Number"  
    ,RANK() OVER (ORDER BY a.PostalCode) AS Rank  
    ,DENSE_RANK() OVER (ORDER BY a.PostalCode) AS "Dense Rank"  
    ,NTILE(4) OVER (ORDER BY a.PostalCode) AS Quartile  
    ,s.SalesYTD  
    ,a.PostalCode  
FROM Sales.SalesPerson AS s   
    INNER JOIN Person.Person AS p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address AS a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL AND SalesYTD <> 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|FirstName|LastName|Row Number|Rank|Dense Rank|Quartile|SalesYTD|PostalCode|  
|---------------|--------------|----------------|----------|----------------|--------------|--------------|----------------|  
|Michael|Blythe|@shouldalert|@shouldalert|@shouldalert|@shouldalert|4557045.0459|98027|  
|Linda|Mitchell|2|@shouldalert|@shouldalert|@shouldalert|5200475.2313|98027|  
|Jillian|Carson|3|@shouldalert|@shouldalert|@shouldalert|3857163.6332|98027|  
|Garrett|Vargas|4|@shouldalert|@shouldalert|@shouldalert|1764938.9859|98027|  
|Tsvi|Reiter|5|@shouldalert|@shouldalert|2|2811012.7151|98027|  
|Shu|Ito|6|6|2|2|3018725.4858|98055|  
|José|Saraiva|7|6|2|2|3189356.2465|98055|  
|David|Campbell|8|6|2|3|3587378.4257|98055|  
|Tete|Mensa-Annan|9|6|2|3|1931620.1835|98055|  
|Lynn|Tsoflias|10|6|2|3|1758385.926|98055|  
|Rachel|Valdez|11|6|2|4|2241204.0424|98055|  
|Jae|Pak|12|6|2|4|5015682.3752|98055|  
|Ranjit|Varkey Chudukatil|13|6|2|4|3827950.238|98055| 


## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-ranking-rows-within-a-partition"></a>D. 对分区中的行进行排名  
 下面的示例根据销售代表的销售总额将每个销售区域中的销售代表进行排名。 行集按 `SalesTerritoryGroup` 分区，按 `SalesAmountQuota` 排序。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryGroup,  
    DENSE_RANK() OVER (PARTITION BY SalesTerritoryGroup ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryGroup != N'NA'  
GROUP BY LastName,SalesTerritoryGroup;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
 LastName          TotalSales     SalesTerritoryGroup  RankResult  
----------------  -------------  -------------------  --------  
Pak               10514000.0000  Europe               1  
Varkey Chudukatil  5557000.0000  Europe               2  
Valdez             2287000.0000  Europe               3  
Carson            12198000.0000  North America        1  
Mitchell          11786000.0000  North America        2  
Blythe            11162000.0000  North America        3  
Reiter             8541000.0000  North America        4  
Ito                7804000.0000  North America        5  
Saraiva            7098000.0000  North America        6  
Vargas             4365000.0000  North America        7  
Campbell           4025000.0000  North America        8  
Ansman-Wolfe       3551000.0000  North America        9  
Mensa-Annan        2753000.0000  North America        10  
Tsoflias           1687000.0000  Pacific              1 
```  

## <a name="see-also"></a>另请参阅  
 [RANK (Transact-SQL)](../../t-sql/functions/rank-transact-sql.md)   
 [ROW_NUMBER (Transact-SQL)](../../t-sql/functions/row-number-transact-sql.md)   
 [NTILE (Transact-SQL)](../../t-sql/functions/ntile-transact-sql.md)   
 [排名函数 (Transact-SQL)](../../t-sql/functions/ranking-functions-transact-sql.md)   
 [函数](../../t-sql/functions/functions.md)  
  
  

