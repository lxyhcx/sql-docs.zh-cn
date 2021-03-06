---
title: 项目设置 (Azure SQL DB) (SybaseToSQL) |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: afce63dc96d2e7d5d95f6a685e625987cd25c7cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>项目设置 (Azure SQL DB) (SybaseToSQL)
Azure SQL DB 项目设置允许你配置要添加在连接对话框，并还允许在 Azure SQL 数据库连接中实现检测信号机制的 Azure SQL DB 数据库后缀。  
  
Azure SQL DB 窗格位于**项目设置**和**默认项目设置**对话框。  
  
-   使用项目设置对话框中设置为当前项目的配置选项。 若要访问 Azure SQL DB 设置中，在**工具**菜单上，选择**项目设置**，单击**常规**底部的左窗格中，，然后选择**Azure SQL DB**。  
  
-   使用默认项目设置对话框中设置的所有项目的配置选项。 若要访问 Azure SQL DB 设置中，在**工具**菜单上，选择**DefaultProject 设置**，单击**常规**底部的左窗格中，，然后选择**Azure SQL DB**。  
  
## <a name="connectivity"></a>连接  
**检测信号间隔**  
  
指定要用于检测信号机制使 Azure SQL 数据库连接中保持活动状态的时间间隔分钟： 秒的格式。  
  
**默认值**:"4:45  
  
应指定的值中正在： ss 的格式 (例如，"4:45 '或' 0:50 ')。  
  
**Azure SQL DB 服务器后缀**  
  
指定 Azure SQL DB 服务器后缀  
  
**默认值**: database.windows.net。  
  
