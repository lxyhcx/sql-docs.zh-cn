---
title: Delete 方法 （ADO 字段集合） |Microsoft 文档
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
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07256948e8b83c6ddac5000bfb12cf590325fd5f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="delete-method-ado-fields-collection"></a>Delete 方法 （ADO 字段集合）
删除从对象[字段](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="syntax"></a>语法  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Parameters  
 *字段*  
 A **Variant**可为指定[字段](../../../ado/reference/ado-api/field-object.md)要删除对象。 此参数可以为的名称**字段**对象或的序号位置**字段**对象本身。  
  
## <a name="remarks"></a>注释  
 调用**Fields.Delete**处于打开状态的方法[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)将导致运行时错误。  
  
## <a name="applies-to"></a>适用范围  
 [字段集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [Delete 方法 （ADO 参数集合）](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete 方法 （ADO 记录集）](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord 方法 (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
