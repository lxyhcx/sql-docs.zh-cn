---
title: 缓存模板、 XSL 和架构 (SQLXML 4.0) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 77e400841542e8e372ccb48f85ffd3a130f9e264
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707895"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>缓存模板、XSL 和架构 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  为了提高性能，[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 支持对模板、XSL 和架构进行缓存。  
  
 所有架构、模板和 XSL 文件（除了来自 http:// 或 ftp:// 位置的文件）都进行缓存。 在运行进程的过程中，缓存的文件保留在内存中。 在进程退出后，所有缓存内容都将丢失。 因此，如果是每个查询都运行一个进程，则缓存带来的好处可能并不明显。  
  
 本节中的主题提供有关缓存的详细信息。  
  
## <a name="in-this-section"></a>本节内容  
 [模板缓存&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 介绍模板缓存并且提供一个用于模板缓存的注册表项。  
  
 [XSL 缓存&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 介绍 XSL 缓存并且提供一个用于 XSL 缓存的注册表项。  
  
 [架构缓存&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 讨论与架构缓存相关的 SQLXML 并行安装问题，并且提供用于架构缓存的注册表项。  
  
  
