---
title: 如何：重写全局代理选择
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c10cff979a18d8e07a1e7089f96157e4c38f040e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-a-global-proxy-selection"></a>如何：重写全局代理选择
此示例将 WebRequest 发送到 www.contoso.com，其在端口 80 上使用名为 `alternateproxy` 的代理服务器替代全局代理选择。  
  
## <a name="example"></a>示例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   引用 System.Net 命名空间。  
  
## <a name="see-also"></a>请参阅  
 [使用应用程序协议](../../../docs/framework/network-programming/using-application-protocols.md)  
 [通过代理访问 Internet](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
