---
title: "默认 SQL Server 数据类型 |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71a28f48cdbfe9e70079abfc392f53976c90c87
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="default-sql-server-data-types"></a>默认 SQL Server 数据类型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

在向服务器发送数据时，如果用户未指定任何 SQL Server 数据类型， [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 会将其 PHP 数据类型中的数据转换为 SQL Server 数据类型。 下表列出了 PHP 数据类型（向服务器发送的数据类型）和默认 SQL Server 数据类型（数据转换到的数据类型）。 有关将数据发送到服务器时如何指定数据类型的详细信息，请参阅 [如何：在使用 SQLSRV 驱动程序时指定 SQL Server 数据类型](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)。  
  
|PHP 数据类型|SQLSRV 驱动程序中的默认 SQL Server 类型|PDO_SQLSRV 驱动程序中的默认 SQL Server 类型|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|不支持|  
|Boolean|bit|bit|  
|Integer|int|int|  
|Float|float(24)|不支持|  
|字符串（长度小于 8000 个字节）|varchar (<string length>)|varchar (<string length>)|  
|字符串（长度大于 8000 个字节）|varchar(max)|varchar(max)|  
|资源|不提供支持。|不提供支持。|  
|流（编码：不是二进制）|varchar(max)|varchar(max)|  
|流（编码：二进制）|varbinary|varbinary|  
|Array|不提供支持。|不提供支持。|  
|对象|不提供支持。|不提供支持。|  
|DateTime (1)|datetime|不提供支持。|  
  
## <a name="see-also"></a>另请参阅  
[常量（Microsoft Drivers for PHP for SQL Server）](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
[PHP 类型](http://go.microsoft.com/fwlink/?LinkId=109071)  
[数据类型 (Transact SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  
