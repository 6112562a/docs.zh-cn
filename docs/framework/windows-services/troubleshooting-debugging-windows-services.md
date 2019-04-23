---
title: 疑难解答：调试 Windows 服务
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: 0552fc005a25e83065bb44e425770f9cef84f71b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082576"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="9bfac-102">疑难解答：调试 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="9bfac-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="9bfac-103">在调试 Windows 服务应用程序时，服务和 Windows 服务管理器交互。</span><span class="sxs-lookup"><span data-stu-id="9bfac-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="9bfac-104">Service Manager 通过调用 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法来启动服务，然后等待 30 秒以便 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法返回。</span><span class="sxs-lookup"><span data-stu-id="9bfac-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="9bfac-105">如果此时该方法未返回，则管理器将显示服务无法启动的错误。</span><span class="sxs-lookup"><span data-stu-id="9bfac-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="9bfac-106">当你调试<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法，如中所述[如何：调试 Windows 服务应用程序](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)中所述调试  方法时，必须注意这 30 秒的时间。</span><span class="sxs-lookup"><span data-stu-id="9bfac-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="9bfac-107">如果在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中放置断点并且未在 30 秒内逐步执行该断点，则管理器将不会启动该服务。</span><span class="sxs-lookup"><span data-stu-id="9bfac-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfac-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="9bfac-108">See also</span></span>

- [<span data-ttu-id="9bfac-109">如何：调试 Windows 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="9bfac-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="9bfac-110">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="9bfac-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
