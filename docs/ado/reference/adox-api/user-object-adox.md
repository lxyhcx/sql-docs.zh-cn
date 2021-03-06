---
title: 用户对象 (ADOX) |Microsoft 文档
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
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 703f62b3a14511bc34aa7f01306ae557db9d07e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="user-object-adox"></a>用户对象 (ADOX)
表示具有受保护的数据库内的访问权限的用户帐户。  
  
## <a name="remarks"></a>注释  
 [用户](../../../ado/reference/adox-api/users-collection-adox.md)集合[目录](../../../ado/reference/adox-api/catalog-object-adox.md)表示目录的所有用户。 **用户**集合[组](../../../ado/reference/adox-api/group-object-adox.md)表示只有特定组的用户。  
  
 与属性、 集合和方法的**用户**对象，你可以：  
  
-   标识与用户[名称](../../../ado/reference/adox-api/name-property-adox.md)属性。  
  
-   更改具有的用户的密码[ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)方法。  
  
-   确定是否用户具有读取、 写入或删除权限[GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)和[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)方法。  
  
-   访问与用户所属组[组](../../../ado/reference/adox-api/groups-collection-adox.md)集合。  
  
-   访问与提供程序特定属性[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合。  
  
-   确定[ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md)用户。  
  
 本部分包含以下主题。  
  
-   [用户对象属性、方法和事件](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [GetPermissions 和 SetPermissions 方法示例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [组集合 (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [用户集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
