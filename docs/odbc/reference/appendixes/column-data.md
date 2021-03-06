---
title: 列数据 |Microsoft 文档
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
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 428f7c4a9d0e21cb989721b095b65bf0c48306fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="column-data"></a>列数据
> [!IMPORTANT]  
>  将 Windows 的未来版本中删除该功能。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 游标库创建在缓存中用于绑定到结果集与每个数据缓冲区的缓冲区**SQLBindCol**。 它使用的值在这些缓冲区中构造**其中**子句时模拟定位更新或删除语句。 它会从数据源和它执行的定位的 update 语句时获取数据时，它会更新这些从行集缓冲区的缓冲区。  
  
 当光标库更新其缓存中的行集缓冲区时，它将根据中指定的 C 数据类型数据传输**SQLBindCol**。 例如，如果行集缓冲区的 C 数据类型，SQL_C_SLONG 游标库传输的数据; 的四个字节如果它是 SQL_C_CHAR 和*BufferLength*为 10，光标库传输 10 个字节的数据。 游标库不传输的数据执行任何类型检查或转换。  
  
> [!NOTE]  
>  游标库不会更新其缓存的列，如果 **StrLen_or_IndPtr*在相应的行集缓冲区是 SQL_DATA_AT_EXEC 或 SQL_LEN_DATA_AT_EXEC 宏的结果。  
  
 当它将更新一个列、 数据源空白填充定长字符数据和根据需要的零填充固定长度的二进制数据。 例如，数据源将 char （10） 列"Smith"存储为"Smith"。 到其缓存此数据复制后执行的定位的更新语句时，游标库将会不空白填充或用零填充行集缓冲区中的数据。 因此，如果应用程序需要的是光标库的缓存中的值是填补空白的或零填充，则它必须空白键盘或用零填充的行集缓冲区中的值在执行的定位的更新语句之前。
