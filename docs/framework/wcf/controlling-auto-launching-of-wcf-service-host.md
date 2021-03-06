---
title: 控制 WCF 服务主机的自动启动
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服务主机的自动启动
在调试包含多个项目的同一个 Visual Studio 解决方案中另一个项目时，你可以控制为 WCF 服务库项目中，Windows Communication Foundation (WCF) 服务主机 (WcfSvcHost.exe) 的自动启动功能。  
  
 为此，请右键单击中的 WCF 服务项目**解决方案资源管理器**，选择**属性**，然后单击**WCF 选项**选项卡。**时启动 WCF 服务主机调试同一解决方案中的另一个项目**复选框默认处于启用状态。 可以清除框中，这样，当在同一解决方案中调试另一个项目时，将不启动此特定项目的 WCF 服务主机。  
  
 此行为不会影响 F5 调试或此项目的“添加服务引用”功能。  
  
 该选项可用于以下项目：  
  
-   WCF 服务库项目。  
  
-   顺序工作流服务库项目。  
  
-   状态机工作流服务库项目。  
  
-   联合服务库项目。  
  
## <a name="see-also"></a>请参阅  
 [WCF 服务主机 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
