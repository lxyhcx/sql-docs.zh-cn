---
title: "连接选项 |Microsoft 文档"
ms.custom: 
ms.date: 07/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aadb44954096cbbcb520850a54d4cc2c41911f08
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="connection-options"></a>连接选项
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主题列出了关联阵列中允许的选项 (使用时[sqlsrv_connect](../../connect/php/sqlsrv-connect.md) SQLSRV 驱动程序中) 或数据源名称 (dsn) 中允许的关键字 (当使用[:: __construct](../../connect/php/pdo-construct.md) PDO_SQLSRV 驱动程序中)。  

|Key|值|说明|默认|  
|-------|---------|---------------|-----------|  
|APP|字符串|指定跟踪中所使用的应用程序名称。|未设置任何值。|  
|ApplicationIntent|字符串|连接到服务器时声明应用程序工作负荷类型。 可能的值为 ReadOnly 和 ReadWrite。<br /><br />有关对 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]支持的详细信息，请参阅 [PHP Driver for SQL Server 对高可用性和灾难恢复的支持](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|ReadWrite|  
|AttachDBFileName|字符串|指定服务器应附加的数据库文件。|未设置任何值。|  
|身份验证|以下字符串之一：<br /><br />SqlPassword<br /><br />ActiveDirectoryPassword|指定的身份验证模式。|未设置。|  
|CharacterSet<br /><br />（在 PDO_SQLSRV 驱动程序中不受支持）|字符串|指定用于将数据发送到服务器的字符集。<br /><br />可能的值为 SQLSRV_ENC_CHAR 和 UTF-8。 有关详细信息，请参阅 [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)。|SQLSRV_ENC_CHAR|  
|ConnectionPooling|1 或 **true** ，表示启用连接池。<br /><br />0 或 **false** ，表示禁用连接池。|指定是否从连接池分配连接 (1 或**true**) 或不 (0 或**false**)。<sup>1</sup>|**true** (1)|  
|数据库|字符串|指定数据库的名称以用于正在建立的连接<sup>2</sup>。|供登录时使用的默认数据库。|  
|Encrypt|1 或 **true** ，表示启用加密。<br /><br />0 或 **false** ，表示禁用加密。|指定是否加密与 SQL Server 的通信 (1 或**true**) 还是解密 (0 或**false**)<sup>3</sup>。|**false** (0)|  
|Failover_Partner|字符串|指定要在主服务器不可用时使用的服务器和数据库镜像的实例（如果已启用且已配置）。<br /><br />对于将 Failover_Partner 与 MultiSubnetFailover 结合使用，存在一些限制。 有关详细信息，请参阅 [PHP Driver for SQL Server 对高可用性和灾难恢复的支持](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|未设置任何值。|  
|LoginTimeout|整数（SQLSRV 驱动程序<br /><br />字符串（PDO_SQLSRV 驱动程序|指定在连接尝试失败前等待的秒数。|无超时。|  
|MultipleActiveResultSets|1 或 **true** ，表示使用多个活动的结果集。<br /><br />0 或 **false** ，表示禁用多个活动的结果集。|禁用或显式启用对多个活动的结果集 (MARS) 的支持。<br /><br />有关详细信息，请参阅[如何： 禁用多个活动结果集 &#40;MARS &#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).|true (1)|  
|MultiSubnetFailover|字符串|始终指定**multiSubnetFailover = yes**连接到的可用性组侦听器时[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]可用性组或[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]故障转移群集实例。 **multiSubnetFailover = yes**配置[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]以便更快地检测和到 （当前） 活动服务器的连接。 可能的值为 Yes 和 No。<br /><br />有关对 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]支持的详细信息，请参阅 [PHP Driver for SQL Server 对高可用性和灾难恢复的支持](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|是|  
|PWD<br /><br />（在 PDO_SQLSRV 驱动程序中不受支持）|字符串|指定与要使用 SQL Server 身份验证连接时要使用的用户 ID 关联的密码<sup>4</sup>。|未设置任何值。|  
|QuotedId|1 或**true**若要使用 SQL 92 规则。<br /><br />0 或 **false** ，表示使用旧规则。|指定是否要用于带引号的标识符的 SQL 92 规则 (1 或**true**) 或使用旧的 Transact SQL 规则 (0 或**false**)。|**true** (1)|  
|ReturnDatesAsStrings<br /><br />（在 PDO_SQLSRV 驱动程序中不受支持）|1 或 **true** ，表示以字符串的形式返回日期和时间类型。<br /><br />0 或 **false** ，表示以 PHP **DateTime** 的形式返回日期和时间类型。|以字符串或 PHP 类型的形式检索日期和时间类型（datetime、date、time、datetime2 和 datetimeoffset）。 当使用 PDO_SQLSRV 驱动程序时，日期将以字符串的形式返回。 PDO_SQLSRV 驱动程序未包含任何**datetime**类型。<br /><br />有关详细信息，请参阅 [如何：使用 SQLSRV 驱动程序以字符串的形式检索日期和时间类型](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)。|**false**|  
|可滚动|字符串|“缓冲”表示你希望使用客户端（缓冲）游标，这将允许你将整个结果集缓存到内存。 有关详细信息，请参阅[游标类型 &#40;SQLSRV 驱动程序 &#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|只进游标|  
|Server<br /><br />（在 SQLSRV 驱动程序中不受支持）|字符串|要连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 实例。<br /><br />你还可以指定要连接到 AlwaysOn 可用性组的虚拟网络名称。 有关对 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]支持的详细信息，请参阅 [PHP Driver for SQL Server 对高可用性和灾难恢复的支持](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|Server 是必需的关键字（尽管它不必是连接字符串中的第一个关键字）。 如果服务器名称未传递给该关键字，尝试连接到本地实例。<br /><br />传递给 Server 的值可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 实例的名称，也可以是该实例的 IP 地址。 你可以选择指定端口号 (例如， `sqlsrv:server=(local),1033`)。<br /><br />从 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的版本 3.0 开始，你还可以指定带有 `server=(localdb)\instancename`的 LocalDB 实例。 有关详细信息，请参阅 [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)。|  
|TraceFile|字符串|指定用于跟踪数据的文件的路径。|未设置任何值。|  
|TraceOn|1 或 **true** ，表示启用跟踪。<br /><br />0 或 **false** ，表示禁用跟踪。|指定是否启用 ODBC 跟踪 (1 或**true**) 还是禁用 (0 或**false**) 正在建立连接。|**false** (0)|  
|TransactionIsolation|SQLSRV 驱动程序使用以下值：<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />PDO_SQLSRV 驱动程序使用以下值：<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|指定事务隔离级别。<br /><br />有关事务隔离的详细信息，请参阅 SQL Server 文档中的 [设置事务隔离级别](http://go.microsoft.com/fwlink/?LinkID=191497) 。|SQLSRV_TXN_READ_COMMITTED<br /><br />或<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**启用**或**已禁用**|影响连接顺序时第一个解析主机名的 IP 未响应并且有多个 ip 地址与主机名。<br /><br />它与 MultiSubnetFailover 提供不同的连接序列进行交互。 有关详细信息，请参阅[使用透明网络 IP 解析](https://docs.microsoft.com/en-us/sql/connect/odbc/using-transparent-network-ip-resolution)。|已启用|
|TrustServerCertificate|1 或 **true** ，表示信任证书。<br /><br />0 或 **false** ，表示不信任证书。|指定客户端是否应信任 (1 或**true**) 或拒绝 (0 或**false**) 的自签名的服务器证书。|**false** (0)|  
|UID<br /><br />（在 PDO_SQLSRV 驱动程序中不受支持）|字符串|指定要使用 SQL Server 身份验证连接时要使用的用户 ID<sup>4</sup>。|未设置任何值。|  
|WSID|字符串|指定用于跟踪的计算机的名称。|未设置任何值。|  

1. `ConnectionPooling`属性不能用于启用/禁用连接池在 Linux 和 mac。 请参阅[连接池 (Microsoft Drivers for PHP for SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)。

2. 建立的连接上执行的所有查询都都会对该数据库中由指定*数据库*属性。 但是，如果用户具有适当的权限，则可以使用完全限定的名称中访问其他数据库中的数据。 例如，如果*master*设置数据库*数据库*连接属性，它将仍然可以执行访问的 TRANSACT-SQL 查询*AdventureWorks.HumanResources.Employee*使用完全限定的名称的表。  

3. 因为加密数据需要计算开销，所以启用 *Encryption* 可能会影响某些应用程序的性能。  

4. 要连接到的 *UID* 身份验证进行连接时，必须同时设置 *PWD* 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 属性。  

许多支持的键都是 ODBC 连接字符串属性。 有关 ODBC 连接字符串的信息，请参阅 [将连接字符串关键字用于 SQL Native Client](http://go.microsoft.com/fwlink/?LinkId=105504)。  

## <a name="see-also"></a>另请参阅  
[连接到服务器](../../connect/php/connecting-to-the-server.md)  
