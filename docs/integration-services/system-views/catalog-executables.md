---
title: catalog.executables | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5c91b11067d29b93eda91fa20d70ea5b5b95eef3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  此视图为指定执行中的每个可执行文件都显示一行。  
  
 可执行文件是添加到包的控制流中的任务或容器。  
  
|列名|**Data type**|Description|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|可执行文件的唯一标识符。|  
|execution_id|**bigint**|执行实例的唯一标识符。|  
|executable_name|**nvarchar(4000)**|可执行文件的名称。|  
|executable_guid|**nvarchar(38)**|可执行文件的 GUID。|  
|package_name|nvarchar(260)|包的名称。|  
|package_path|**nvarchar(max)**|包的路径。|  
  
## <a name="permissions"></a>权限  
 此视图需要下列权限之一：  
  
-   针对执行实例的 READ 权限  
  
-   ssis_admin 数据库角色的成员资格  
  
-   sysadmin 服务器角色的成员资格  
  
> [!NOTE]  
>  当您具有在服务器上执行操作的权限时，您还具有查看有关此操作的信息的权限。 将实施行级安全性；只显示您有权查看的行。  
  
## <a name="remarks"></a>Remarks  
  
