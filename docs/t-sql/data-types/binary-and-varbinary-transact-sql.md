---
title: binary 和 varbinary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 8/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- binary_TSQL
- varbinary_TSQL
- binary
- varbinary
dev_langs:
- TSQL
helpviewer_keywords:
- varbinary data type
- binary [SQL Server], about binary data type
ms.assetid: bcce65f9-10db-4b3e-bfaf-dfc06c6f820f
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 624a2b764d6c397b950796fe822764b7983664ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="binary-and-varbinary-transact-sql"></a>binary 和 varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定长度或可变长度的 Binary 数据类型。
  
## <a name="arguments"></a>参数  
binary [ ( n ) ] 长度为 n 字节的固定长度二进制数据，其中 n 是从 1 到 8,000 的值。 存储大小为 n 字节。
  
varbinary [ ( n | max) ] 可变长度二进制数据。 n 的取值范围为 1 至 8,000。 max 指示最大存储大小是 2^31-1 个字节。 存储大小为所输入数据的实际长度 + 2 个字节。 所输入数据的长度可以是 0 字节。 varbinary 的 ANSI SQL 同义词为 binary varying。
  
## <a name="remarks"></a>Remarks  
如果没有在数据定义或变量声明语句中指定 n，则默认长度为 1。 如果没有使用 CAST 函数指定 n，则默认长度为 30。

| 数据类型 | 何时使用... |
| --- | --- |
| **binary** | 列数据项的大小一致。|
| **varbinary** | 列数据项的大小差异相当大。|
| **varbinary(max)** | 列数据条目超出 8,000 字节。|


## <a name="converting-binary-and-varbinary-data"></a>转换 binary 和 varbinary 数据
将数据从字符串数据类型（char、varchar、nchar、nvarchar、binary、varbinary、text、ntext 或图像）转换为不等长的 binary 或 varbinary 数据类型时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会在数据的右侧填充或截断数据。 从其他数据类型转换为 binary 或 varbinary 时，将在数据的左侧填充或截断数据。 填充将通过使用十六进制的零来完成。
  
如果 binary 数据是最容易来回移动的数据，则将数据转换为 binary 和 varbinary 数据类型很有用。 将任一类型的任一值转换为足够大的二进制值，然后转换回原类型时，如果两次转换都是在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本上进行的，则始终生成相同的值。 值的二进制表示形式在不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本之间可能会有所不同。
  
可以将 int、smallint 和 tinyint 转换为 binary 或 varbinary，但是如果将 binary 转换回整数值，则在发生了截断的情况下此值将不同于原始整数值。 例如，以下 SELECT 语句显示整数值 `123456` 通常被存储为二进制值 `0x0001e240`：
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
但是，以下 `SELECT` 语句显示如果 binary 目标太小而不能保存整个值，则前导数字会被自动截断，以使该数值存储为 `0xe240`：
  
```sql
SELECT CAST( 123456 AS BINARY(2) );  
```  
  
以下批处理显示，这种自动截断会影响算术运算而不产生错误：
  
```sql
DECLARE @BinaryVariable2 BINARY(2);  
  
SET @BinaryVariable2 = 123456;  
SET @BinaryVariable2 = @BinaryVariable2 + 1;  
  
SELECT CAST( @BinaryVariable2 AS INT);  
GO  
```  
  
最终结果为 `57921`，而不是 `123457`。
  
> [!NOTE]  
>  不能保证在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 各个版本之间对任一数据类型与 binary 数据类型进行转换的结果是一致的。  
  
## <a name="see-also"></a>另请参阅
[CAST 和 CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[数据类型转换（数据库引擎）](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  
