---
title: 支持的数据类型 |Microsoft 文档
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
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b11c3df36ba36153f71721d9a10dee702ef745d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-types"></a>支持的数据类型
支持的 Dbms 的数据类型大不相同。 应用程序可以通过调用中确定的名称和受支持的数据类型特征**SQLGetTypeInfo**。 由于数据类型名称的宽变体，该应用程序必须使用返回的数据类型名称**SQLGetTypeInfo**中**CREATE TABLE**语句。 有关详细信息，请参阅[ODBC 中的数据类型](../../../odbc/reference/develop-app/data-types-in-odbc.md)。
