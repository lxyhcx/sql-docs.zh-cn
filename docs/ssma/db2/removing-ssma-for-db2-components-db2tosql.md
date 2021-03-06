---
title: 为 DB2 组件 (DB2ToSQL) 删除 SSMA |Microsoft 文档
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7b727dbe1edf24fb8fafb5c219aed8cb1e8bf5a3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>为 DB2 组件 (DB2ToSQL) 删除 SSMA
完成后将数据库迁移到 DB2 从[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]，你可能想要卸载 SSMA 组件。 你可以随时卸载客户端组件。 但是，你不应卸载来自的扩展包[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]除非你已迁移的数据库不再使用中的函数**ssma_DB2**架构**sysdb**数据库。  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>卸载 SSMA DB2 客户端  
你可以通过使用卸载 SSMA**添加或删除程序**。  
  
**若要卸载 SSMA**  
  
1.  在 Control Panel 中，打开**添加或删除程序**。  
  
2.  选择 **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for DB2**，然后单击**删除**。  
  
3.  若要确认你想要卸载 SSMA，单击**是**。  
  
## <a name="uninstalling-the-extension-pack"></a>卸载扩展包  
如果您确信你已迁移的数据库不使用中的对象**sysdb.ssma_DB2**架构，你可以删除从架构中移除的扩展包 – 有是没有 Windows 卸载  
  
## <a name="see-also"></a>另请参阅  
[安装适用于 DB2 客户端 SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[在 SQL Server 上安装 SSMA 组件&#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
