---
title: 创建度量值语句 (MDX) |Microsoft 文档
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98ca479c266d9e8c25b2e75d8b15da1cd76a46aa
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579349"
---
# <a name="mdx-data-definition---create-measure"></a>MDX 数据定义-创建度量值
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  在表格模型中创建度量值。  
  
## <a name="syntax"></a>语法  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>参数  
 *Table_Name*  
 一个有效的字符串，用于提供要创建度量值的表的名称。  
  
 *Measure_Name*  
 提供度量值名称的有效字符串。  
  
 *DAX_Expression*  
 返回单个标量值的有效的 DAX 表达式。  
  
## <a name="remarks"></a>Remarks  
 *Measure_Name*必须用正方形括号括起来。  
  
 创建度量值语句只能在 MDX 脚本定义; 内部使用请参阅[MdxScript 元素&#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md)。  
  
 还可以定义供一个查询使用的计算成员。 若要定义只供一个查询使用的计算成员，请在 SELECT 语句中使用 WITH 子句。 有关详细信息，请参阅[在 MDX 中生成度量值](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md)。  
  
## <a name="see-also"></a>请参阅  
 [MDX 数据定义语句&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
