---
title: "catalog.move_environment （SSISDB 数据库） |Microsoft 文档"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e08328e0baccaa9098d8647b50c6133de2504912
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveenvironment-ssisdb-database"></a>catalog.move_environment（SSISDB 数据库）
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  将环境从一个文件夹移到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录中的另一个文件夹。  
  
## <a name="syntax"></a>语法  
  
```tsql  
move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>参数  
 [ @source_folder =] *source_folder*  
 此环境在移动之前所在的源文件夹的名称。 *Source_folder*是**nvarchar （128)**。  
  
 [ @environment_name =] *environment_name*  
 要移动的环境的名称。 *Environment_name*是**nvarchar （128)**。  
  
 [ @destination_folder =] *destination_folder*  
 此环境在移动之后所在的目标文件夹的名称。 *Destination_folder*是**nvarchar （128)**。  
  
## <a name="return-code-value"></a>返回代码值  
 0（成功）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="permissions"></a>Permissions  
 此存储过程需要下列权限之一：  
  
-   针对环境的 READ 和 MODIFY 权限  
  
-   成员资格**ssis_admin**数据库角色  
  
-   成员资格**sysadmin**服务器角色  
  
## <a name="errors-and-warnings"></a>错误和警告  
 下面的列表描述了一些可能引发错误或警告的情况：  
  
-   在源文件夹中不存在此环境  
  
-   目标文件夹中已存在同名的环境  
  
-   用户没有适当的权限  
  
## <a name="remarks"></a>注释  
 在移动过程中，项目中的环境引用未遵循此环境。 必须相应地更新环境引用。 即使通过移动环境损坏了环境引用，此存储过程也会成功。 在此存储过程完成之后，必须更新环境引用。  
  
> [!NOTE]  
>  项目可以具有相对或绝对的环境引用。 相对引用通过名称引用环境，这些引用要求环境与项目位于相同文件夹中。 绝对引用通过名称和文件夹引用环境，这些引用引用与项目不在同一文件夹中的环境。  
  
  