---
title: SQLEndTran （光标库） |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fe61f62906c113d7ea07c96f20f816456c6bfb1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran （光标库）
> [!IMPORTANT]  
>  将 Windows 的未来版本中删除该功能。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 本主题讨论使用**SQLEndTran**光标库中的函数。 有关常规信息**SQLEndTran**，请参阅[SQLEndTran 函数](../../../odbc/reference/syntax/sqlendtran-function.md)。  
  
 游标库不支持事务，并将传递到调用**SQLEndTran**直接向驱动程序。 然而，光标库支持游标提交和回滚行为由具有 SQL_CURSOR_ROLLBACK_BEHAVIOR 和 SQL_CURSOR_COMMIT_BEHAVIOR 信息类型的数据源返回：  
  
-   对于跨事务保留游标的数据源，将回滚数据源中的更改不会回滚光标库的缓存中。 若要使数据源中的数据匹配的缓存，应用程序必须关闭并重新打开光标。  
  
-   对于关闭游标的事务边界的数据源，游标库关闭游标，并删除缓存的连接上的所有语句。  
  
-   对于删除已准备的语句在事务边界的数据源，应用程序必须 reprepare 之前 reexecuting 它们连接上的所有已准备的语句。
