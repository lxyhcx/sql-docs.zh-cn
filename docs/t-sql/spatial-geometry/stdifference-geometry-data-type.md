---
title: "STDifference (geometry 数据类型) |Microsoft 文档"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geometry Data Type)
ms.assetid: 737f39bb-8750-4ffb-8594-23febc2f1075
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c6b79813c903e5c5541b2aab8d09ba1858f28f0
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="stdifference-geometry-data-type"></a>STDifference（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回一个对象，表示该点集从一个**几何图形**不在另一个实例**几何图形**实例。
  
## <a name="syntax"></a>语法  
  
```  
  
.STDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>参数  
 *other_geometry*  
 是另一种**几何图形**实例，该值指示该点以从在其上实例中删除`STDifference()`从中调用。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返回类型：**几何图形**  
  
 CLR 返回类型： **SqlGeometry**  
  
## <a name="remarks"></a>注释  
 如果此方法将始终返回 null 的空间引用 Id 为 (Srid)**几何图形**实例不匹配。   只有在输入实例包含圆弧线段时，结果才会包含圆弧线段。  
  
## <a name="examples"></a>示例  
  
### <a name="a-computing-the-difference-between-two-polygon-instances"></a>A. 计算两个 Polygon 实例的差集  
 以下示例使用 `STDifference()` 计算两个多边形的差集。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-invoking-stdifference-on-a-curvepolygon-instance"></a>B. 在 CurvePolygon 实例上调用 STDifference()  
 以下示例在 CurvePolygon 实例上使用 STDifference()。  
  
 `DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';`  
  
 `DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';`  
  
 `-- Note the different results returned by the two SELECT statements`  
  
 `SELECT @h.STDifference(@g).ToString(), @g.STDifference(@h).ToString();`  
  
## <a name="see-also"></a>另请参阅  
 [在几何图形实例的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

