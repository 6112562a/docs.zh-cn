---
title: 如何：重写全局代理选择
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: bda2da2400c97b3cc0ad2bbc573283cff8035310
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129059"
---
# <a name="how-to-override-a-global-proxy-selection"></a>如何：重写全局代理选择
此示例将 WebRequest 发送到 `www.contoso.com`，其在端口 80 上使用名为 `alternateproxy` 的代理服务器替代全局代理选择。  
  
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
  
-   System.Net 命名空间的 [`using` 指令](~/docs/csharp/language-reference/keywords/using-directive.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用应用程序协议](../../../docs/framework/network-programming/using-application-protocols.md)  
 [通过代理访问 Internet](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
