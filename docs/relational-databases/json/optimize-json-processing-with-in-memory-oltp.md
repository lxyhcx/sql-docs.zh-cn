---
title: "使用内存中 OLTP 优化 JSON 处理 | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-vnext
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4e0331c288665fd9f69444d0d14366dfa69a668f
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>使用内存中 OLTP 优化 JSON 处理
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

SQL Server 和 Azure SQL 数据库允许使用 JSON 格式的文本。 为了提高处理 JSON 数据的 OLTP 查询的性能，可以使用标准字符串列（NVARCHAR 类型）将 JSON 文档存储在内存优化表中。

## <a name="store-json-in-memory-optimized-tables"></a>在内存优化表中存储 JSON
下面的示例演示了包含两个 JSON 列（`Tags` 和 `Data`）的 `Product` 内存优化表：

```tsql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```
将 JSON 数据存储在内存优化表中可以利用无锁内存中数据访问来提高查询性能。

## <a name="optimize-json-with-additional-in-memory-features"></a>使用其他内存中功能优化 JSON
使用 SQL Server 和 Azure SQL 数据库中的新功能可将 JSON 功能与现有的内存中 OLTP 技术完全集成。 例如，可以执行以下操作：
 - 使用本机编译的 CHECK 约束验证内存优化表中存储的 JSON 文档的结构。
 - 使用计算列公开和强类型化 JSON 文档中存储的值。
 - 使用内存优化索引为 JSON 文档中的值编制索引。
 - 本机编译使用 JSON 文档中的值或者将结果设置为 JSON 文本格式的 SQL 查询。

## <a name="validate-json-columns"></a>验证 JSON 列
SQL Server 和 Azure SQL 数据库允许添加本机编译的 CHECK 约束，用于验证字符串列中存储的 JSON 文档的内容，如下面的示例中所示。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

可在包含 JSON 列的现有表中添加本机编译的 CHECK 约束：

```tsql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

使用本机编译的 JSON CHECK 约束，可以确保内存优化表中存储的 JSON 文本的格式正确。

## <a name="expose-json-values-using-computed-columns"></a>使用计算列公开 JSON 值
使用计算列可以公开 JSON 文本中的值和访问这些值，而无需重新计算从 JSON 文本中提取值的表达式，且无需重新分析 JSON 结构。 公开强类型化的、以物理方式持久保存在计算列中的值。 使用持久化计算列访问 JSON 值的速度比访问 JSON 文档中的值要快。

下面的示例演示如何公开 JSON `Data` 列中的以下两个值：
-   制造产品的国家/地区。
-   产品制造成本。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

每当 `MadeIn` 列中存储的 JSON 文档发生更改时，计算列 `Cost` 和 `Data` 就会更新。

## <a name="index-values-in-json-columns"></a>为 JSON 列中的值编制索引
SQL Server 和 Azure SQL 数据库允许使用内存优化索引为 JSON 列中的值编制索引。 必须使用计算列公开和强类型化要编制索引的 JSON 值，如下面的示例中所示。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```
可以使用标准 NONCLUSTERED 和 HASH 索引为 JSON 列中的值编制索引。
-   NONCLUSTERED 索引可以优化按某个 JSON 值选择行范围或者按 JSON 值将结果排序的查询。
-   通过指定要查找的确切值提取单个行或少量行时，HASH 索引可以提供最佳性能。

## <a name="native-compilation-of-json-queries"></a>本机编译 JSON 查询
最后，使用 JSON 函数本机编译包含查询的 Transact-SQL 过程、函数和触发器可以提高查询性能，减少执行这些过程所需的 CPU 周期。 下面的示例演示使用多个 JSON 函数（JSON_VALUE、OPENJSON 和 JSON_MODIFY）的本机编译过程。

```tsql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="next-steps"></a>后续步骤
内存中 OLTP 本机模块中的 JSON 针对 SQL Server 和 Azure SQL 数据库中的内置 JSON 功能提供性能改进。

若要详细了解 JSON 的核心使用方案，请查看以下资源：

-   [TechNet 博客](https://blogs.technet.microsoft.com/dataplatforminsider/2016/01/05/json-in-sql-server-2016-part-1-of-4/)
-   [MSDN 文档](https://msdn.microsoft.com/library/dn921897.aspx)
-   [第 9 频道视频](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

若要了解将 JSON 集成到应用程序的各种方案，请查看以下资源：
-   参阅这部[第 9 频道视频](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)中的演示。
-   在 [JSON 博客文章](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)中查找与你的用例匹配的方案。
-   在 [GitHub 存储库](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/json/)中查找示例。

