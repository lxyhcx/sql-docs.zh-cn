---
title: 验证用户输入 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 438f65ae8ec719339297b62e9bef7c347a063a1b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="validating-user-input"></a>验证用户输入
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  当您构造访问数据的应用程序时，应假定所有用户输入在获得验证之前都是恶意的。 未做到这一点可能导致应用程序易受攻击。 一个类型的攻击会被称为 SQL 注入恶意代码添加到更高版本传递到的实例的字符串的下[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]进行分析和运行。 为了避免这种类型的攻击，应尽可能使用带参数的存储过程，并始终验证用户输入。  
  
 在客户端代码中验证用户输入是非常重要的，这样，您就无需浪费时间往返服务器。 在服务器上验证存储过程的参数以捕获无效的和跳过客户端验证的输入，这同样非常重要。  
  
 有关 SQL 注入以及如何避免它的详细信息，请参阅 》 的"SQL 注入"[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]联机丛书。 有关验证存储的过程参数的详细信息，请参阅"存储过程 ([!INCLUDE[ssDE](../../includes/ssde_md.md)])"和从属中的主题[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]联机丛书。  
  
## <a name="see-also"></a>另请参阅  
 [保护 JDBC 驱动程序应用程序](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
