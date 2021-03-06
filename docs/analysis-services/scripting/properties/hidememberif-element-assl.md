---
title: HideMemberIf 元素 (ASSL) |Microsoft 文档
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7c2e76ae7cd667327f2eaf464ba790a34d0b253c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="hidememberif-element-assl"></a>HideMemberIf 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指示是否应该从客户端应用程序中隐藏某一级别的成员以及何时隐藏。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|String（枚举）|  
|默认值|*永远不会*|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[级别](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 此元素的值限定为下表中的字符串之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|*永远不会*|从不隐藏成员。|  
|*OnlyChildWithNoName*|如果成员是其父级的唯一子级并且成员名称为空，则隐藏该成员。|  
|*OnlyChildWithParentName*|如果成员是其父级的唯一子级并且其名称与其父级名称相同，则隐藏该成员。|  
|*NoName*|如果成员名称为空，则隐藏该成员。|  
|*ParentName*|如果成员名称与其父级名称相同，则隐藏该成员。|  
  
## <a name="remarks"></a>注释  
 对应于的允许值为枚举**HideMemberIf**在分析管理对象 (AMO) 对象模型并<xref:Microsoft.AnalysisServices.HideIfValue>。  
  
## <a name="see-also"></a>另请参阅  
 [属性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
