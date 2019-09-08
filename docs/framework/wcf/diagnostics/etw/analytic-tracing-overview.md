---
title: 分析跟踪概述
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 6170accc01e837bba0afb446f67a6c6272e7dde7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798202"
---
# <a name="analytic-tracing-overview"></a>分析跟踪概述
[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析跟踪是基于 Windows 事件跟踪 (ETW) 的高性能、低详细级别的跟踪功能。 ETW 在内核级别运行，极大地减少了跟踪操作的开销。 它有效缓冲用户模式和内核模式的事件，并允许动态启用日志记录，而无需重新启动服务。 发出并接收跟踪数据之后，即可在事件日志中获取这些数据。  
  
 有关 ETW 的详细信息，请参阅[通过 Etw 改善调试和性能优化](https://go.microsoft.com/fwlink/?LinkId=164781)。  
  
 除使用 Windows 的“系统”、“安全性”和“应用程序”事件日志分析应用程序外， [!INCLUDE[wv](../../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] 还在“应用程序和服务日志”顶级节点下引入了其他日志。 这些新日志的用途在于存储特定应用程序或特定组件的事件，而不是存储具有系统范围影响的全局事件（如“安全性”事件日志可能记录的事件类型）。 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]将 wcf 跟踪事件、wcf 消息日志和[!INCLUDE[wf1](../../../../../includes/wf1-md.md)]跟踪记录的日志记录统一和关联到应用程序和服务日志。  
  
## <a name="concepts-and-capabilities"></a>概念和功能  
 以下概念和功能适用于 WCF 分析跟踪。  
  
### <a name="enabling-wcf-diagnostics-settings"></a>启用 WCF 诊断设置  
 WCF 诊断在 system.servicemodel > \<\<诊断 > 配置部分中启用。  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Web 承载的 IIS 虚拟应用程序的 WCF 诊断设置在该应用程序的 Web.config 文件中启用。 另一选择是在应用程序的子目录中创建 Web.config。  此选择会将这些设置应用于子目录中的所有服务。  若要确保对应用程序中的所有服务以一致的方式初始化诊断设置，诊断设置应位于应用程序目录中的 Web.config 内，而不是位于应用程序的其中一个单独子目录中。  
  
### <a name="channels"></a>信道  
 ETW 允许软件组件利用通道将跟踪事件定向到特定用户。 例如，您可以将面向系统管理员的事件发送到一个通道，而将应用程序开发人员关注的事件发送到另一个通道。 通道在 Windows 中命名和注册，因此使用者可以使用事件查看器查看通道的事件。  
  
 WCF 的分析跟踪功能[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]写入到 Microsoft Windows-应用程序-服务器-应用程序通道。 此通道专为想要在生产中监视 WCF 服务运行状况的用户设计。 它定义了一组少量事件，可用于多种运行状况监视和疑难解答情况。  
  
 若要针对 Windows 清单启用事件跟踪以便在事件日志中对消息正确解码，请在命令行上使用 ServiceModelReg 工具，如下所示：  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>动态配置  
 ETW 基础结构允许使用标准 Windows 工具动态启用和配置跟踪。 有关详细信息，请参阅[动态启用分析跟踪](dynamically-enabling-analytic-tracing.md)。  
  
### <a name="message-flow-tracing"></a>消息流跟踪  
 有关如何启用消息流跟踪的详细信息，请参阅[配置消息流跟踪](configuring-message-flow-tracing.md)。  
  
### <a name="keywords"></a>关键字  
 关键字用于筛选跟踪消息，并定义 .NET Framework 发出事件的组件。 有关详细信息，请参阅[动态启用分析跟踪](dynamically-enabling-analytic-tracing.md)。
