---
title: Index 属性 |Microsoft 文档
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
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01e7883719900e85fdb7227f50c90ed265f73c30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="index-property"></a>索引属性
指示当前对有效的索引名称[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回**字符串**值，该值是索引的名称。  
  
## <a name="remarks"></a>注释  
 通过名为索引**索引**属性必须之前已声明对基表基础**记录集**对象。 也就是说，索引必须已经声明以编程方式为 ADOX[索引](../../../ado/reference/adox-api/index-object-adox.md)对象，或创建基本表时。  
  
 如果索引不能设置，将发生运行时错误。 **索引**以下情况下，不能设置属性：  
  
-   在[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)或**RecordsetChangeComplete**事件处理程序。  
  
-   如果**记录集**仍在执行操作 (其可以通过确定[状态](../../../ado/reference/ado-api/state-property-ado.md)属性)。  
  
-   如果对设置了筛选器**记录集**与[筛选器](../../../ado/reference/ado-api/filter-property.md)属性。  
  
 **索引**如果，属性可以始终成功设置**记录集**已关闭，但**记录集**不会成功，打开或索引将不可用，如果基础提供程序不支持索引。  
  
 如果可以设置索引，可能会更改的当前行位置。 这将导致对的更新[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)属性，并且会触发**WillChangeRecordset**， **RecordsetChangeComplete**， [WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)，和[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)事件。  
  
 如果可以设置索引和[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)属性是**adLockPessimistic**或**adLockOptimistic**，然后隐式[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)执行操作。 这将释放的当前和受影响的组。 释放任何现有的筛选器，并且当前行位置更改为重新排序后的第一行**记录集**。  
  
 **索引**结合使用属性[Seek](../../../ado/reference/ado-api/seek-method.md)方法。 如果基础提供程序不支持**索引**属性，因此**Seek**方法，请考虑使用[查找](../../../ado/reference/ado-api/find-method-ado.md)方法相反。 确定是否**记录集**对象支持与索引[支持](../../../ado/reference/ado-api/supports-method.md)**(adIndex)** 方法。  
  
 内置**索引**属性不相关为动态[优化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)属性，尽管它们都应对索引。  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [查找方法和索引的属性示例 (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [索引对象 (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek 方法](../../../ado/reference/ado-api/seek-method.md)
