---
title: SQL Server R Services 中的 R 互操作性 | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59196e0569ac9cc683b3affa68fc17f068e74994
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="r-interoperability-in-sql-server"></a>SQL Server 中的 R 互操作性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本主题侧重于运行 SQL Server 中的 R 的机制，并介绍 Microsoft R 和开放源代码。 之间的差异

适用于： SQL Server 2016 R Services、 SQL Server 自 2017 年 1 机器学习服务

有关其他组件的信息，请参阅[SQL Server 中的新组件](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md)。

### <a name="open-source-r-components"></a>开放源代码 R 组件

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] 包括基础 R 包和工具的完整发行版。 有关基础发行版包含哪些组件的详细信息，请参阅安装期间在以下默认位置安装的文档：`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

在安装 [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] 的过程中，必须同意 GNU 公共版的许可条款。 然后，无需进一步的修改即可运行标准 R 包，就像运行 R 的其他任何开源发行版一样。

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 不会以任何方式修改 R 运行时。 R 运行时在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 进程的外部执行，并且可独立于 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 运行。 但是，我们强烈建议不要在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 使用 R 时运行这些工具，以免发生资源争用。

可在与实例关联的文件夹中找到与特定 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 实例关联的 R 基础包发行版。 例如，如果在默认实例上安装 R Services，R 库位于此文件夹中默认情况下：

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

同样，与默认实例关联的 R 工具将位于此应用文件夹中默认情况下：

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

有关如何 Microsoft R 是不同于你可能获得 CRAN 的 R 基础分发的详细信息，请参阅[R 语言和 Microsoft R 产品和功能的互操作性](https://docs.microsoft.com/en-us/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>从 Microsoft R 的其他 R 包

除了基本的 R 分发，[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]包括某些专有的 R 包，以及一个框架，用于并行执行还支持远程计算上下文执行的 R 的 R。

R 功能的这种组合（R 基础分发版加上增强的 R 功能和包）称为 **Microsoft R**。如果安装了 Microsoft R Server（独立版），获得的包集与连同 SQL Server R Services（数据库内）一起安装的包集完全相同，但这些包安装在不同的文件夹中。

Microsoft R 包含 Intel 数学内核库的发行版，每当能够加速数学处理时，就会使用该库。 例如，基本线性代数 (BLAS) 库用于许多附加包以及 R 本身。 有关详细信息，请参阅以下文章：

+ [How the Intel Math Kernel Speeds up R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)（Intel 数学内核库如何加速 R）
+ [Performance benefits of linking R to multithreaded math libraries](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)（将 R 链接到多线程数学库所带来的性能优势）

在 Microsoft R 中，最重要的补充包是 **RevoScaleR** 和 **RevoPemaR** 包。 这些 R 包主要使用 C 或 C++ 编写，目的是提高性能。

+ **RevoScaleR。** 包含用于数据处理和分析的各种 API。 这些 API 已经过优化，可以分析由于过大而无法装入内存的数据集，以及执行分布在多个核心或处理器之间的计算。

   RevoScaleR API 还支持处理数据的子集，从而提高了可伸缩性。 换而言之，大多数 RevoScaleR 函数可针对数据区块运行，并使用更新算法来聚合结果。 因此，基于 RevoScaleR 函数的 R 解决方案可以处理极大型数据集，并且不受本地内存的约束。

  RevoScaleR 包还支持使用 .XDF 文件格式来加速移动和存储用于分析的数据。 XDF 格式使用纵栏表存储且可移植，可用于加载并处理来自各种来源（包括文本、SPSS 或 ODBC 连接）的数据。 

+ **RevoPemaR。** PEMA 是“并行外部内存算法”的缩写。 **RevoPemaR** 包提供可用于开发你自己的并行算法的 API。 有关详细信息，请参阅 [RevoPemaR Getting Started Guide](https://docs.microsoft.com/r-server/r/how-to-developer-pemar)（RevoPemaR 入门指南）。

我们还建议你尝试[MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)，从支持远程执行的 R 代码和可伸缩性，与分布式处理的 Microsoft R 新的包使用改进的机器学习算法由 Microsoft Research 开发。

## <a name="next-steps"></a>后续步骤

[体系结构概述](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[SQL Server 中支持 R 组件](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[安全性概述](../../advanced-analytics/r/security-overview-sql-server-r.md)

