---
title: 使用中立即 AddNew 和批处理模式 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c66b250780e3b12ae9590796a062426f89920de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>使用中立即 AddNew 和批处理模式
行为**AddNew**方法取决于的更新模式**记录集**对象和是否传递*FieldList*和*值*自变量。  
  
 在立即更新模式下 (在其中提供程序将更改写入基础数据源一旦调用**更新**方法)，则调用**AddNew**方法，而自变量集**EditMode**属性**adEditAdd。** 提供程序将任何字段值更改在本地缓存。 调用**更新**方法发送到数据库的新记录，并将重置**EditMode**属性**adEditNone。** 如果你通过*FieldList*和*值*自变量，ADO 立即发送到数据库的新记录 (没有**更新**调用是必需的); **EditMode**属性值不会更改 (**adEditNone**)。  
  
 在批处理更新模式下，调用**AddNew**方法，而自变量集**EditMode**属性**adEditAdd**。 提供程序将任何字段值更改在本地缓存。 调用**更新**方法将新的记录添加到当前**记录集**并重置**EditMode**属性**adEditNone**，但提供程序不会发送到基础数据库更改，直到你调用**UpdateBatch**方法。 如果你通过*FieldList*和*值*自变量，ADO 将新记录发送到缓存中的存储提供程序; 你需要调用**UpdateBatch**发布新的方法记录到基础数据库。 有关详细信息**更新**和**UpdateBatch**，请参阅[更新和保持数据](../../../ado/guide/data/updating-and-persisting-data.md)。
