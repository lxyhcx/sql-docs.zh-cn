---
title: "NEWID (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWID
- NEWID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- NEWID function
ms.assetid: f7014e60-96d5-457e-afc3-72b60ba20c0f
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6f9b19f1af5bc0b9c3bde1dfd7bddabd420f40d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="newid-transact-sql"></a>NEWID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  创建类型的唯一值**uniqueidentifier**。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
NEWID ( )  
```  
  
## <a name="return-types"></a>返回类型  
 **uniqueidentifier**  
  
## <a name="remarks"></a>注释  
 `NEWID()` 遵从 RFC4122。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-the-newid-function-with-a-variable"></a>A. 对变量使用 NEWID 函数  
 下面的示例使用`NEWID()`将值分配给变量声明为**uniqueidentifier**数据类型。 值**uniqueidentifier**测试值，在打印数据类型的变量。  
  
```  
-- Creating a local variable with DECLARE/SET syntax.  
DECLARE @myid uniqueidentifier  
SET @myid = NEWID()  
PRINT 'Value of @myid is: '+ CONVERT(varchar(255), @myid)  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Value of @myid is: 6F9619FF-8B86-D011-B42D-00C04FC964FF  
```  
  
> [!NOTE]  
>  NEWID 对每台计算机返回的值各不相同。 所显示的数字仅起解释说明的作用。  
  
### <a name="b-using-newid-in-a-create-table-statement"></a>B. 在 CREATE TABLE 语句中使用 NEWID  
  
**适用于**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
 下面的示例创建`cust`表与**uniqueidentifier**数据类型，并使用 NEWID 表填充默认值。 为 `NEWID()` 赋予默认值时，每个新行和现有行均对 `CustomerID` 列具有唯一值。  
  
```  
-- Creating a table using NEWID for uniqueidentifier data type.  
CREATE TABLE cust  
(  
 CustomerID uniqueidentifier NOT NULL  
   DEFAULT newid(),  
 Company varchar(30) NOT NULL,  
 ContactName varchar(60) NOT NULL,   
 Address varchar(30) NOT NULL,   
 City varchar(30) NOT NULL,  
 StateProvince varchar(10) NULL,  
 PostalCode varchar(10) NOT NULL,   
 CountryRegion varchar(20) NOT NULL,   
 Telephone varchar(15) NOT NULL,  
 Fax varchar(15) NULL  
);  
GO  
-- Inserting 5 rows into cust table.  
INSERT cust  
(CustomerID, Company, ContactName, Address, City, StateProvince,   
 PostalCode, CountryRegion, Telephone, Fax)  
VALUES  
 (NEWID(), 'Wartian Herkku', 'Pirkko Koskitalo', 'Torikatu 38', 'Oulu', NULL,  
 '90110', 'Finland', '981-443655', '981-443655')  
,(NEWID(), 'Wellington Importadora', 'Paula Parente', 'Rua do Mercado, 12', 'Resende', 'SP',  
 '08737-363', 'Brasil', '(14) 555-8122', '')  
,(NEWID(), 'Cactus Comidas para Ilevar', 'Patricio Simpson', 'Cerrito 333', 'Buenos Aires', NULL,   
 '1010', 'Argentina', '(1) 135-5555', '(1) 135-4892')  
,(NEWID(), 'Ernst Handel', 'Roland Mendel', 'Kirchgasse 6', 'Graz', NULL,  
 '8010', 'Austria', '7675-3425', '7675-3426')  
,(NEWID(), 'Maison Dewey', 'Catherine Dewey', 'Rue Joseph-Bens 532', 'Bruxelles', NULL,  
 'B-1180', 'Belgium', '(02) 201 24 67', '(02) 201 24 68');  
GO  
```  
  
### <a name="c-using-uniqueidentifier-and-variable-assignment"></a>C. 使用 uniqueidentifier 和变量赋值  
 下面的示例声明名的本地变量`@myid`的变量作为**uniqueidentifier**数据类型。 然后使用 `SET` 语句为该变量赋值。  
  
```  
DECLARE @myid uniqueidentifier ;  
SET @myid = 'A972C577-DFB0-064E-1189-0154C99310DAAC12';  
SELECT @myid;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [NEWSEQUENTIALID &#40;Transact SQL &#41;](../../t-sql/functions/newsequentialid-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [强制转换和转换 &#40;Transact SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [System Functions (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [uniqueidentifier &#40;Transact SQL &#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)   
 [序列号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  