---
title: 通道扩展性
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: aeff683b786d81fc782914bd2df70adb10bcbcec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944048"
---
# <a name="channels-extensibility"></a>通道扩展性
本节包含演示自定义通道的示例。  
  
## <a name="in-this-section"></a>本节内容  
 [本地通道](../../../../docs/framework/wcf/samples/local-channel.md)  
 演示本地通道，使用相同的应用程序域内进行通信的 WCF 传输通道。  
  
 [可靠安全配置文件](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 演示如何编写 WCF 和可靠安全配置文件 (RSP)。  
  
 [自定义通道调度程序](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 演示如何通过直接实现 <xref:System.ServiceModel.ServiceHostBase> 以自定义方式生成通道堆栈，以及如何在 Web 主机环境中创建自定义通道调度程序。  
  
 [区块通道](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 演示如何限制用于使用 WCF 发送大消息进行缓冲的内存量。
  
 [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 演示如何生成自定义协议通道，以便使用 HTTP Cookie 进行会话管理。  
  
 [自定义消息拦截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 演示如何实现可创建通道工厂和通道侦听器的自定义绑定元素，以便在运行时堆栈的特定点截获所有传入和传出消息。
