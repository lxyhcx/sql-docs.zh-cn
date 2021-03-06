---
title: 标量函数转义序列 |Microsoft 文档
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
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ca98389b0279ded2aba487e2e3e0f6bbbe95e6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="scalar-function-escape-sequence"></a>标量函数转义序列
ODBC 标量函数使用转义序列。 此转义序列的语法如下所示：  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>注释  
 BNF 表示法中的语法，如下所示是：  
  
 *ODBC 标量函数转义*:: =  
  
 *ODBC esc 启动器*fn*标量函数 ODBC esc 终止符*  
  
 *标量函数*:: =*函数名称*(*自变量列表*)  
  
 (非终止符的定义*函数名称*和*函数名称*(*自变量列表*) 派生自的中的标量函数的列表[附录 e： 标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)。)  
  
 *ODBC esc 启动器*:: = {  
  
 *ODBC esc 终止符*:: =}  
  
 若要确定是否数据源支持过程的驱动程序支持 ODBC 过程调用语法，应用程序可以调用**SQLGetInfo**。 有关详细信息，请参阅[附录 e： 标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)。
