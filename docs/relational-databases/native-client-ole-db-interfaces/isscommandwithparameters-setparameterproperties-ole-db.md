---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dbd38ed336375cef79119f2fafb565bceeeb85bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  按照序号基于每个参数设置参数属性，或者通过指定 SSPARAMPROPS 结构数组来设置大容量参数属性。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>参数  
 *cParams*[in]  
 SSPARAMPROPS 数结构中*rgParamProperties*数组。 如果此数字为零， **ISSCommandWithParameters::SetParameterProperties**将删除已为命令中的任何参数指定的所有属性。  
  
 *rgParamProperties*[in]  
 要设置的 SSPARAMPROPS 结构数组。  
  
## <a name="return-code-values"></a>返回代码值  
 **ISSCommandWithParameters::SetParameterProperties**方法返回作为核心 OLE DB 相同的错误代码**ICommandProperties::SetProperties**方法。  
  
## <a name="remarks"></a>備註  
 使用此方法设置参数属性基于每个参数允许序号，或使用单个**ISSCommandWithParameters::SetParameterProperties**调用后 SSPARAMPROPS 由属性数组。  
  
 **SetParameterInfo**方法必须调用，然后再调**ISSCommandWithParameters::SetParameterProperties**方法。 调用 `SetParameterProperties(0, NULL)` 可清除所有指定的参数属性，而调用 `SetParameterInfo(0,NULL,NULL)` 则会清除所有参数信息（包括可能与某个参数相关的任何属性）。  
  
 调用**ISSCommandWithParameters::SetParameterProperties**为一个参数的类型不是该参数指定属性 DBTYPE_XML 或以外，dbtype_udt 还返回以 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED 和标记*dwStatus*为该参数与 DBPROPSTATUS_NOTSET SSPARAMPROPS 中包含的所有 DBPROPs 字段。 应当遍历 SSPARAMPROPS 中包含的每个 DBPROPSET 的 DBPROP 数组，以检测 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED 引用了哪些参数。  
  
 如果**ISSCommandWithParameters::SetParameterProperties**调用指定的参数与，尚未尚未设置其参数信息的属性**SetParameterInfo**，该提供程序返回 E_意外出现以下错误消息：  
  
 在没有先调用 SetParameterInfo 方法的情况下，不能为指定参数调用 SetParameterProperties 方法。 在设置参数属性之前，必须首先设置参数信息。  
  
 如果调用**ISSCommandWithParameters::SetParameterProperties**包含参数信息已设置，某些参数以及其中的参数信息尚未设置中的 dwStatus 属性某些参数DBSTATUS_NOTSET 将返回 DBPROPSET SSPARAMPROPS 属性集。  
  
 SSPARAMPROPS 结构的定义如下所示：  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 从数据库引擎中的改进[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]允许 ISSCommandWithParameters::SetParameterProperties 以获取更准确的预期结果的说明。 这些更准确的结果可能与在以前版本的 ISSCommandWithParameters::SetParameterProperties 返回的值不同[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 有关详细信息，请参阅[元数据发现](../../relational-databases/native-client/features/metadata-discovery.md)。  
  
|成员|Description|  
|------------|-----------------|  
|*iOrdinal*|所传递参数的序号。|  
|*cPropertySets*|DBPROPSET 数结构中*rgPropertySets*。|  
|*rgPropertySets*|指向内存中将返回 DBPROPSET 结构数组的位置的指针。|  
  
## <a name="see-also"></a>另请参阅  
 [ISSCommandWithParameters & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
