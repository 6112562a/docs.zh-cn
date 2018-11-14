---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: 902225085ccaceb9d90d0c25d9369ef65ae2730b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193105"
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> 类提供一个可通过编程方式控制的 HTTP 协议侦听器。 侦听器在 <xref:System.Net.HttpListener> 对象的生存期内处于活动状态，在你的应用程序中运行。  
  
## <a name="httpsys"></a>HTTP.SYS  
 <xref:System.Net.HttpListener> 类在 HTTP.sys 的基础上构建，后者是为 Windows 处理所有 HTTP 流量的内核模式侦听器。 HTTP.sys 提供连接管理、带宽限制以及 Web 服务器日志记录。 使用 `HttpCfg.exe` 工具可添加 SSL 证书。 有关详细信息，请参阅[服务器](https://go.microsoft.com/fwlink/?LinkID=178285)文档中的 [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) 工具相关文档。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [HTTP 服务器](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [Internet 信息中的安全性增强功能](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [HttpListener ASPX 主机应用程序示例](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [HttpListener 技术示例](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [网络编程示例](../../../docs/framework/network-programming/network-programming-samples.md)
