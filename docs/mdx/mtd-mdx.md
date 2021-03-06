---
title: Mtd (MDX) |Microsoft 文档
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e38d8d3485e50054ee4d1106b1ef7bdfc8ce96ea
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580759"
---
# <a name="mtd-mdx"></a>Mtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  按照时间维度中的年级别的约束，从给定成员所在的级别返回一组同级成员，从第一个同级成员开始到给定成员为止。  
  
## <a name="syntax"></a>语法  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>Remarks  
 如果未指定一个成员表达式，默认值是第一个层次结构使用的类型级别的当前成员*月*中类型的第一个维度*时间*度量值组中。  
  
 **Mtd**函数是快捷函数[PeriodsToDate](../mdx/periodstodate-mdx.md)函数时级别所基于的属性层次结构的类型属性设置为*月*。 也就是说，`Mtd(Member_Expression)` 等效于 `PeriodsToDate(Month_Level_Expression,Member_Expression)`。  
  
## <a name="example"></a>示例  
 下例将返回 2002 年 7 月（截止于 2002 年 7 月 20 日）Internet 销售的当月运费成本总和。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [Sum &#40;MDX&#41;](../mdx/sum-mdx.md)   
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
