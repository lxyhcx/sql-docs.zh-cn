---
title: EntityType 元素 (CSDLBI) |Microsoft 文档
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 60d1b91ab417343a9dffe7e83520ebcd868c5d6d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="entitytype-element-csdlbi"></a>EntityType 元素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  **EntityType**元素是复杂类型，表示高级实体，例如客户或订单，在数据模型的结构。 **Bi: EntityType**元素扩展的定义[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)中使用[实体数据框架](http://msdn.microsoft.com/library/bb399567.aspx)。  
  
 必须为数据模型中包括的每个实体指定 EntityType 元素。 EntityType 的子元素描述表中的列和度量值。 在表之间的关系将包括在**EntityContainer**。  
  
## <a name="elements-and-attributes"></a>元素和属性  
 下表列出的元素和特性定义**EntityType**元素。 另请参阅适用于属性[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)元素。  
  
|名称|是否必需|Description|  
|----------|-----------------|-----------------|  
|目录|否|一个包含列中可能的数据类型的字符串。 此值从数据模型中 DimensionAttributeTypeEnumType 的值派生。<br /><br /> 如果 DimensionAttributeTypeEnumType 的值为“ExtendedType”，则 Contents 的值从 DimensionAttribute 的 ExtendedType 元素派生。 客户端不需要对这些值进行回应。|  
|DefaultDetails|否|表示表中一组列的属性引用的列表。<br /><br /> 请参阅[DefaultDetails 元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/defaultdetails-element-csdlbi.md).|  
|DefaultImage|否|对包含用来说明该实体的图像的列的引用。<br /><br /> 在多维模型中，此元素对应于维度属性上的一个二进制属性。 如果此属性存在，则此元素必须只包含一个 MemberRef 元素。<br /><br /> 请参阅[MemberRef 元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DefaultMeasure|否|对实体中某个度量值的引用，当对该实体进行计算时，此度量值应用作默认值。 如果未指定，则默认值为 SUM。<br /><br /> 请参阅[MemberRef 元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DisplayKey|否|对列或对角色方的引用列表，这构成了一个强标识符，此标识符可唯一标识实体实例。<br /><br /> 请参阅[DisplayKey 元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/displaykey-element-csdlbi.md).|  
|层次结构|否|模型中层次结构的列表。<br /><br /> 请参阅[层次结构元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).|  
|ReferenceName|是|可用于在数据分析表达式 (DAX) 查询中引用此实体的标识符。<br /><br /> 如果此属性不存在，则使用此实体的完全限定字段名称。|  
|SortMembers|否|要排序的属性列表。 SortDirection 属性指示是升序还是降序。|  
  
## <a name="contents-element"></a>Contents 元素  
 **内容**元素是一个简单类型，描述实体中的数据的类型。  
  
 实体（列）的内容可以是以下任何值：  
  
|“值”|Description|  
|-----------|-----------------|  
|Regular|未定义。|  
|Time|属性表示时间段（如年、半期、季度、月或天）。|  
|Geography|属性表示地域信息（如市县或邮政编码）。|  
|单位|属性表示单位信息（如雇员或分公司）。|  
|BillOfMaterials|属性表示库存或制造信息（如产品的部件列表）。|  
|帐户|属性表示用于财务报表用途的科目表。|  
|客户|属性表示客户信息或联系信息。|  
|产品|属性表示产品信息。|  
|应用场景|属性表示计划或策略分析信息。|  
|定量|属性表示定量信息。|  
|实用工具|属性表示其他信息。|  
|货币|包含货币数据和元数据。|  
|汇率|属性表示汇率信息。|  
|渠道|属性表示渠道信息。|  
|促销|属性表示营销促销信息。|  
  
## <a name="example"></a>示例  
 **表格**  
  
 以下示例显示在 AdventureWorks 表格模型中使用的 Geography 表的 CSDLBI 版本 1.1 表示形式的一部分。 RowNumber 列是隐藏的列生成，自动为在表格模型中，行标识符并因此具有内容属性中， **RowNumber**。  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>示例  
 **多维**  
  
 以下示例显示 CSDLBI 版本 1.1 中的 EntityType 元素，这些元素表示 Contoso Operations 多维数据集中时间维度的一部分。  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>另请参阅  
 [BI 批注的 CSDL 的技术参考](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
