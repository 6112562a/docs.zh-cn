---
title: 分析跟踪概述
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: f6ffed3d9f0bf5e3dc5698d51276eb1db276993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837488"
---
# <a name="analytic-tracing-overview"></a><span data-ttu-id="e8721-102">分析跟踪概述</span><span class="sxs-lookup"><span data-stu-id="e8721-102">Analytic Tracing Overview</span></span>
<span data-ttu-id="e8721-103">[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析跟踪是基于 Windows 事件跟踪 (ETW) 的高性能、低详细级别的跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="e8721-103">Analytic tracing in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] is a high performance and low verbosity tracing feature set on top of Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="e8721-104">ETW 在内核级别运行，极大地减少了跟踪操作的开销。</span><span class="sxs-lookup"><span data-stu-id="e8721-104">ETW runs at the kernel-level to greatly reduce the overhead of tracing operations.</span></span> <span data-ttu-id="e8721-105">它有效缓冲用户模式和内核模式的事件，并允许动态启用日志记录，而无需重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="e8721-105">It efficiently buffers user- and kernel-mode events, and allows dynamic enabling of logging without requiring service restarts.</span></span> <span data-ttu-id="e8721-106">发出并接收跟踪数据之后，即可在事件日志中获取这些数据。</span><span class="sxs-lookup"><span data-stu-id="e8721-106">The tracing data is available in the event logs after it has been emitted and received.</span></span>  
  
 <span data-ttu-id="e8721-107">有关 ETW 的详细信息，请参阅[通过 Etw 改善调试和性能优化](https://go.microsoft.com/fwlink/?LinkId=164781)。</span><span class="sxs-lookup"><span data-stu-id="e8721-107">For more information about ETW, see [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkId=164781).</span></span>  
  
 <span data-ttu-id="e8721-108">除了使用 Windows 系统、安全性和应用程序事件日志分析应用程序外，Windows Vista 和 [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] 还在应用程序和服务日志顶级节点下引入了其他日志。</span><span class="sxs-lookup"><span data-stu-id="e8721-108">In addition to using the Windows System, Security, and Application event logs to analyze application, Windows Vista and [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduced additional logs under the Applications and Services Logs top-level node.</span></span> <span data-ttu-id="e8721-109">这些新日志的用途在于存储特定应用程序或特定组件的事件，而不是存储具有系统范围影响的全局事件（如“安全性”事件日志可能记录的事件类型）。</span><span class="sxs-lookup"><span data-stu-id="e8721-109">The purpose of these new logs is to store events for a particular application or specific component instead of global events that have a system-wide impact (such as the type of events that the Security event log might record).</span></span> [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="e8721-110">将 WCF 跟踪事件、WCF 消息日志和 [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 跟踪记录的日志记录统一和关联到应用程序和服务日志。</span><span class="sxs-lookup"><span data-stu-id="e8721-110">unifies and correlates the logging of WCF Trace Events, WCF Message Logs, and [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Tracking records to the Applications and Services Logs.</span></span>  
  
## <a name="concepts-and-capabilities"></a><span data-ttu-id="e8721-111">概念和功能</span><span class="sxs-lookup"><span data-stu-id="e8721-111">Concepts and Capabilities</span></span>  
 <span data-ttu-id="e8721-112">以下概念和功能适用于 WCF 分析跟踪。</span><span class="sxs-lookup"><span data-stu-id="e8721-112">The following concepts and capabilities apply to WCF Analytic Tracing.</span></span>  
  
### <a name="enabling-wcf-diagnostics-settings"></a><span data-ttu-id="e8721-113">启用 WCF 诊断设置</span><span class="sxs-lookup"><span data-stu-id="e8721-113">Enabling WCF Diagnostics Settings</span></span>  
 <span data-ttu-id="e8721-114">WCF 诊断在 \<System.servicemodel >\<诊断 > 配置部分中启用。</span><span class="sxs-lookup"><span data-stu-id="e8721-114">WCF diagnostics are enabled within the \<system.serviceModel>\<diagnostics> configuration section.</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 <span data-ttu-id="e8721-115">Web 承载的 IIS 虚拟应用程序的 WCF 诊断设置在该应用程序的 Web.config 文件中启用。</span><span class="sxs-lookup"><span data-stu-id="e8721-115">WCF diagnostic settings for a Web-hosted IIS virtual application are enabled in its’ Web.config file.</span></span> <span data-ttu-id="e8721-116">另一选择是在应用程序的子目录中创建 Web.config。</span><span class="sxs-lookup"><span data-stu-id="e8721-116">Another option is to create a Web.config in a sub-directory within the application.</span></span>  <span data-ttu-id="e8721-117">此选择会将这些设置应用于子目录中的所有服务。</span><span class="sxs-lookup"><span data-stu-id="e8721-117">This choice applies the settings to all of the services within a sub-directory.</span></span>  <span data-ttu-id="e8721-118">若要确保对应用程序中的所有服务以一致的方式初始化诊断设置，诊断设置应位于应用程序目录中的 Web.config 内，而不是位于应用程序的其中一个单独子目录中。</span><span class="sxs-lookup"><span data-stu-id="e8721-118">To ensure that the diagnostics settings are initialized consistently for all services within the application, the settings should be within the Web.config in the application directory and not in one of the individual sub-directories within the application.</span></span>  
  
### <a name="channels"></a><span data-ttu-id="e8721-119">Channels</span><span class="sxs-lookup"><span data-stu-id="e8721-119">Channels</span></span>  
 <span data-ttu-id="e8721-120">ETW 允许软件组件利用通道将跟踪事件定向到特定用户。</span><span class="sxs-lookup"><span data-stu-id="e8721-120">ETW allows software components to direct tracing events to a particular audience by use of channels.</span></span> <span data-ttu-id="e8721-121">例如，您可以将面向系统管理员的事件发送到一个通道，而将应用程序开发人员关注的事件发送到另一个通道。</span><span class="sxs-lookup"><span data-stu-id="e8721-121">For example, you can send events for system administrators to one channel, and events that application developers care about to another channel.</span></span> <span data-ttu-id="e8721-122">通道在 Windows 中命名和注册，因此使用者可以使用事件查看器查看通道的事件。</span><span class="sxs-lookup"><span data-stu-id="e8721-122">Channels are named and registered with Windows so that consumers can view a channel’s events using the Event Viewer.</span></span>  
  
 <span data-ttu-id="e8721-123">[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 中的 WCF 的分析跟踪功能将写入到 Microsoft Windows-应用程序-服务器-应用程序通道。</span><span class="sxs-lookup"><span data-stu-id="e8721-123">The analytic tracing feature for WCF in [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] writes to the Microsoft-Windows-Application-Server-Applications channel.</span></span> <span data-ttu-id="e8721-124">此通道专为想要在生产中监视 WCF 服务运行状况的用户设计。</span><span class="sxs-lookup"><span data-stu-id="e8721-124">This channel is specifically designed for users who want to monitor the health of WCF services in production.</span></span> <span data-ttu-id="e8721-125">它定义了一组少量事件，可用于多种运行状况监视和疑难解答情况。</span><span class="sxs-lookup"><span data-stu-id="e8721-125">It defines a small, set of events that can be used in many health monitoring and troubleshooting scenarios.</span></span>  
  
 <span data-ttu-id="e8721-126">若要针对 Windows 清单启用事件跟踪以便在事件日志中对消息正确解码，请在命令行上使用 ServiceModelReg 工具，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e8721-126">To enable the Event Tracing for Windows manifest so that messages are decoded properly in the event log, use the ServiceModelReg tool on the command line as follows:</span></span>  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="e8721-127">动态配置</span><span class="sxs-lookup"><span data-stu-id="e8721-127">Dynamic Configuration</span></span>  
 <span data-ttu-id="e8721-128">ETW 基础结构允许使用标准 Windows 工具动态启用和配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="e8721-128">The ETW infrastructure allows tracing to be enabled and configured dynamically using standard Windows tools.</span></span> <span data-ttu-id="e8721-129">有关详细信息，请参阅[动态启用分析跟踪](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="e8721-129">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>  
  
### <a name="message-flow-tracing"></a><span data-ttu-id="e8721-130">消息流跟踪</span><span class="sxs-lookup"><span data-stu-id="e8721-130">Message Flow Tracing</span></span>  
 <span data-ttu-id="e8721-131">有关如何启用消息流跟踪的详细信息，请参阅[配置消息流跟踪](configuring-message-flow-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="e8721-131">For more information about how to enable message flow tracing, see [Configuring Message Flow Tracing](configuring-message-flow-tracing.md).</span></span>  
  
### <a name="keywords"></a><span data-ttu-id="e8721-132">关键字</span><span class="sxs-lookup"><span data-stu-id="e8721-132">Keywords</span></span>  
 <span data-ttu-id="e8721-133">关键字用于筛选跟踪消息，并定义 .NET Framework 发出事件的组件。</span><span class="sxs-lookup"><span data-stu-id="e8721-133">Keywords are used to filter trace messages and define which component of the .NET Framework emitted the event.</span></span> <span data-ttu-id="e8721-134">有关详细信息，请参阅[动态启用分析跟踪](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="e8721-134">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>
