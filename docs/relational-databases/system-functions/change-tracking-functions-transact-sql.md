---
title: 更改跟踪函数 (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c478d4ca59db55cefe5e13444fd81ea7bf64dbea
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "33227256"
---
# <a name="change-tracking-functions-transact-sql"></a>更改跟踪函数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  更改跟踪函数用于记录应用于被跟踪表的插入、更新和删除操作，同时采用易于使用的关系格式提供有关更改的详细信息。 下列函数返回有关更改的信息。  
  
|函数|Description|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES)](../../relational-databases/system-functions/changetable-transact-sql.md)|返回自指定版本起对表所做的所有更改的跟踪信息。|  
|[CHANGETABLE （版本）](../../relational-databases/system-functions/changetable-transact-sql.md)|返回指定行的最新更改跟踪信息。|  
|[CHANGE_TRACKING_MIN_VALID_VERSION()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|返回用于获取更改跟踪信息从指定的表，当你使用有效的最低版本[CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)函数。|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|获取与上次提交事务关联的版本。 可以在下次使用 CHANGETABLE 枚举更改时使用此版本。|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|用于解释由 CHANGETABLE(CHANGES …) 函数返回的 SYS_CHANGE_COLUMNS 值。|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|用于在应用程序更改数据时指定更改上下文，例如发起方 ID。|  
  
## <a name="see-also"></a>请参阅  
 [跟踪数据更改 (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
