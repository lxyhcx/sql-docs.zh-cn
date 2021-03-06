---
title: 如何： 流的形式发送数据 |Microsoft 文档
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data
- streaming data
ms.assetid: ab6b95d6-b6e6-4bd7-a18c-50f2918f7532
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10e4c00840658ac4cb74707d0a5dfdc49d448c34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-send-data-as-a-stream"></a>如何：以流的形式发送数据
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 利用 PHP 流将大型对象发送到服务器。 本主题中的示例演示如何以流的形式发送数据。 第一个示例使用 SQLSRV 驱动程序演示默认行为，即在查询执行时发送所有流数据。 第二个示例使用 SQLSRV 驱动程序来演示如何发送最多八千字节 (8 kB) 的流数据到服务器的一次。  
  
第三个示例演示如何使用 PDO_SQLSRV 驱动程序将流数据发送到服务器。  
  
## <a name="example-sending-stream-data-at-execution"></a>示例： 在执行发送流数据
以下示例向 AdventureWorks 数据库的 *Production.ProductReview* 表中插入一行。 客户意见 (*$comments*) 以通过 PHP 流的形式打开[fopen](http://php.net/manual/en/function.fopen.php)函数，然后流式传输到服务器在执行查询时。  
  
该示例假定 SQL Server 和[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)数据库安装在本地计算机上。 所有输出都写入控制台。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$comments = fopen( "data://text/plain,[ Insert lengthy comment here.]",  
                  "r");  
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Execute the query. All stream data is sent upon execution.*/  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
else  
{  
     echo "The query was successfully executed.";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example-sending-stream-data-using-sqlsrvsendstreamdata"></a>示例： 发送流数据使用 sqlsrv_send_stream_data
下一个示例是前面的示例中，相同，但在执行发送所有流数据的默认行为已关闭。 该示例使用 [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md) 将流数据发送到服务器。 最多八个字节 (8 kB) 的数据发送到每次调用**sqlsrv_send_stream_data**。 该脚本将对 **sqlsrv_send_stream_data** 发出的调用数进行计数并将该计数显示到控制台。  
  
该示例假定 SQL Server 和[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)数据库安装在本地计算机上。 所有输出都写入控制台。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$comments = fopen( "data://text/plain,[ Insert lengthy comment here.]",  
                  "r");  
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Turn off the default behavior of sending all stream data at  
execution. */  
$options = array("SendStreamParamsAtExec" => 0);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params, $options);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Send up to 8K of parameter data to the server with each call to  
sqlsrv_send_stream_data. Count the calls. */  
$i = 1;  
while( sqlsrv_send_stream_data( $stmt))   
{  
     echo "$i call(s) made.\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
虽然本主题中的示例将字符数据发送到服务器，但任何格式的数据都可以采用流的形式发送。 例如，你还可以使用本主题中所演示的技术以流的形式发送采用二进制格式的图像。  
  
## <a name="example-sending-an-image-as-a-stream"></a>示例： 以流的形式发送图像 
  
```  
<?php  
   $server = "(local)";   
   $database = "Test";  
   $conn = new PDO( "sqlsrv:server=$server;Database = $database", "", "");  
  
   $binary_source = fopen( "data://text/plain,", "r");  
  
   $stmt = $conn->prepare("insert into binaries (imagedata) values (?)");  
   $stmt->bindParam(1, $binary_source, PDO::PARAM_LOB);   
  
   $conn->beginTransaction();  
   $stmt->execute();  
   $conn->commit();  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[更新数据（Microsoft Drivers for PHP for SQL Server）](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[使用 SQLSRV 驱动程序以流的形式检索数据](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[文档中相关的代码示例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
