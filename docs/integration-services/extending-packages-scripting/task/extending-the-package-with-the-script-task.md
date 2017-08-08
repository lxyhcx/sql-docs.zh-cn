---
title: "Extending the Package with the Script Task |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>使用脚本任务扩展包
  脚本任务扩展的运行时功能[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]用自定义代码编写的包[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual Basic 或[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual C#，编译并在包运行时执行。 当 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含的任务不能满足您的要求时，脚本任务可简化自定义运行时任务的开发。 脚本任务可用于编写所有必需的基础结构代码，这样您就可以只将注意力集中于自定义处理所需的代码。  
  
 脚本任务与包含程序包通过全局交互**Dts**对象、 实例<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>在脚本环境中公开的类。 可以在脚本任务中编写用于修改存储在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 变量中的值的代码；稍后，包可使用这些更新值来确定其工作流的路径。 脚本任务还可以使用 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 命名空间、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 类库以及自定义程序集来实现自定义功能。  
  
 脚本任务及其生成的基础结构代码可大大简化自定义任务的开发过程。 但是，若要了解脚本任务的工作原理，你可能发现很有用读取部分[开发自定义任务](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)了解开发自定义任务涉及的步骤。  
  
 如果要创建计划在多个包中重用的任务，则应考虑开发自定义任务，而不使用脚本任务。 有关详细信息，请参阅[比较脚本解决方案和自定义对象](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)。  
  
## <a name="in-this-section"></a>本節內容  
 下列主题提供有关脚本任务的详细信息。  
  
 [在脚本任务编辑器中配置脚本任务](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 说明如何在配置的属性**脚本任务编辑器**影响功能和脚本任务中的代码的性能。  
  
 [编码和调试脚本任务](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 说明如何使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 开发的脚本任务中包含的脚本。  
  
 [在脚本任务中使用变量](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性使用变量。  
  
 [连接到在脚本任务中的数据源](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 属性使用连接。  
  
 [在脚本任务中引发事件](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 属性引发事件。  
  
 [在脚本任务中的日志记录](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法记录信息。  
  
 [从脚本任务中返回结果](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 说明如何通过 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 属性和 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性返回结果。  
  
 [脚本任务示例](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 提供一些简单的示例，演示脚本任务的几种可能用法。  
  
## <a name="see-also"></a>另請參閱  
 [脚本任务](../../../integration-services/control-flow/script-task.md)   
 [比较脚本任务和脚本组件](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  