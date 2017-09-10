---
title: "ENCRYPTBYCERT (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYCERT
- ENCRYPTBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], encryption
- encryption [SQL Server], certificates
- ENCRYPTBYCERT function
ms.assetid: ab66441f-e2d2-4e3a-bcae-bcc09e12f3c1
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a0165a370081fc32974cccbfdfd4f97abf0e1b9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="encryptbycert-transact-sql"></a>ENCRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用证书的公钥加密数据。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
EncryptByCert ( certificate_ID , { 'cleartext' | @cleartext } )  
```  
  
## <a name="arguments"></a>参数  
 *certificate_ID*  
 数据库中证书的 ID。 **int**。  
  
 *明文形式*  
 将使用证书进行加密的数据字符串。  
  
 **@cleartext**  
 类型的变量的**nvarchar**， **char**， **varchar**，**二进制**， **varbinary**，或**nchar**包含将使用该证书的公钥加密的数据。  
  
## <a name="return-types"></a>返回类型  
 **varbinary** 8000 个字节的最大大小。  
  
## <a name="remarks"></a>注释  
 该函数使用证书的公钥对数据进行加密。 只能使用相应的私钥对加密文本进行解密。 此类非对称转换较比使用对称密钥进行加密和解密的方法，其开销更大。 因此，建议在处理大型数据集（如多个表中的用户数据）时不使用非对称加密。  
  
## <a name="examples"></a>示例  
 此示例将以称为 `@cleartext` 的证书对在 `JanainaCert02` 中存储的纯文本进行加密。 经过加密的数据将插入表 `ProtectedData04` 中。  
  
```  
INSERT INTO [AdventureWorks2012].[ProtectedData04]   
    VALUES ( N'Data encrypted by certificate ''Shipping04''',  
    EncryptByCert(Cert_ID('JanainaCert02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [DECRYPTBYCERT &#40;Transact SQL &#41;](../../t-sql/functions/decryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [删除证书 &#40;Transact SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  