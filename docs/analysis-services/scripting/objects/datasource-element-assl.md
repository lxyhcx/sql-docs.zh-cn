---
title: "数据源元素 (ASSL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DataSource Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataSource
helpviewer_keywords:
- DataSource element
ms.assetid: 113fba1c-2679-4d06-9339-90a4a76f9b31
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c436c4083d6763cebabe8bf33f69e6090e21bebe
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="datasource-element-assl"></a>DataSource 元素 (ASSL)
  定义中的数据源[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [数据库](../../../analysis-services/scripting/objects/database-element-assl.md)元素。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<DataSources>  
   <DataSource xsi:type="RelationalDataSource">...</DataSource>  
   <!-- or -->  
   <DataSource xsi:type="OlapDataSource">...</DataSource>  
   <!-- or -->  
   <DataSource xsi:type="PushedDataSource">...</DataSource>  
</DataSources>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|[RelationalDataSource](../../../analysis-services/scripting/data-type/relationaldatasource-data-type-assl.md)， [OlapDataSource](../../../analysis-services/scripting/data-type/olapdatasource-data-type-assl.md)， [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
|默认值|无|  
|基数|0-n：可多次出现的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[数据源](../../../analysis-services/scripting/collections/datasources-element-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 分析管理对象 (AMO) 对象模型中的相应元素是<xref:Microsoft.AnalysisServices.DataSource>。  
  
## <a name="see-also"></a>另请参阅  
 [数据库元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [对象 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  