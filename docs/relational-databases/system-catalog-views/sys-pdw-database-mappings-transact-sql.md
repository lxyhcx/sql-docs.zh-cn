---
title: sys.pdw_database_mappings (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f1455d25c0a3ea344c5104053358b2d4fed0c65b
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="syspdwdatabasemappings-transact-sql"></a>sys.pdw_database_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  地图**database_id**s 数据库的物理名称到计算节点上使用，并提供**主体 id**系统上的数据库所有者。 加入**sys.pdw_database_mappings**到**sys.databases**和**sys.pdw_nodes_pdw_physical_databases**。  
  
|列名|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|计算节点上数据库的物理名称。<br /><br /> **physical_name**和**database_id**窗体中的密钥，此视图。||  
|database_id|**int**|数据库的对象 ID。 请参阅[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)。<br /><br /> **physical_name**和**database_id**窗体中的密钥，此视图。||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下面的示例将 sys.pdw_database_mappings 联接到其他系统表以显示数据库的映射方式。  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库目录视图](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_index_mappings &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys.pdw_table_mappings &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_nodes_pdw_physical_databases &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

