---
title: 国际支持 （Visual FoxPro ODBC 驱动程序） |Microsoft 文档
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
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151d3989737d221e46f6771055d0775c69f7e576
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>国际支持 （Visual FoxPro ODBC 驱动程序）
Microsoft Visual FoxPro ODBC 驱动程序支持：  
  
-   双字节字符集 (DBCS)  
  
-   多个排序规则序列  
  
 排序规则序列定义*排序顺序*Visual FoxPro 表或数据库中存储的数据。 默认情况下，该驱动程序配置为使用支持你的操作系统的语言版本的排序规则序列。  
  
 有关支持的排序规则序列的列表，请参阅[设置 COLLATE](../../odbc/microsoft/set-collate-command.md)。  
  
## <a name="locale"></a>区域设置 (locale)  
 对应于给定的语言和国家/地区的信息的组。 区域设置指示诸如的小数点分隔符、 日期和时间格式，以及字符排序顺序的特定设置。  
  
## <a name="sort-order"></a>排序顺序 (sort order)  
 排序顺序包含不同的排序规则*区域设置*的使您可以正确这些语言的数据进行排序。 Visual FoxPro 中当前的排序顺序确定字符表达式比较和索引或排序表的记录中显示在其中的顺序的结果。
