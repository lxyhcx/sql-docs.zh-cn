---
title: 注释 (MDX) |Microsoft 文档
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a38b7c7ed805afbcdfd3b5426141358bfde742c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577439"
---
# <a name="comment-mdx"></a>注释 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  表示用户提供的注释文本。  
  
## <a name="syntax"></a>语法  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Parameters  
 *Comment_Text*  
 包含注释文本的字符串。  
  
## <a name="remarks"></a>Remarks  
 服务器不会评估之间注释字符的文本 / * 和\*/。 注释可以插入到单独一行中，也可以插入到多维表达式 (MDX) 语句中。 必须由指示多行注释 /\*和\*/。  
  
 注释没有最大长度限制。 注释可以嵌套，例如，`/* Test /*Comment*/ Text*/` 就是一个嵌套注释的例子。  
  
## <a name="examples"></a>示例  
 下面的示例演示了此运算符的用法。  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>请参阅  
 [&#40;注释&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [--（注释）(MDX)](../mdx/comment-mdx-operator-reference.md)   
 [MDX 运算符参考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
