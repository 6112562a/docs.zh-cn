---
title: 如何：启动服务
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 3544f7d846ecf68ed5ed01812b9c69b295c63c69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952415"
---
# <a name="how-to-start-services"></a><span data-ttu-id="5a3fe-102">如何：启动服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-102">How to: Start Services</span></span>
<span data-ttu-id="5a3fe-103">安装服务后，必须启动它。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="5a3fe-104">开始调用服务类上的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="5a3fe-105"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法通常定义服务将执行的有用工作。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="5a3fe-106">服务启动后，在手动暂停或停止它前，该服务将保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="5a3fe-107">服务可以设置为自动或手动启动。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="5a3fe-108">自动启动的服务将在安装它的计算机重启或首次打开时启动。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="5a3fe-109">用户必须启动手动启动的服务。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a3fe-110">默认情况下，使用 Visual Studio 创建的服务设置为手动启动。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-110">By default, services created with Visual Studio are set to start manually.</span></span>  
  
 <span data-ttu-id="5a3fe-111">可以通过多种方式手动启动服务 — 从“服务器资源管理器”  、“服务控制管理器”  ，或从使用名为 <xref:System.ServiceProcess.ServiceController> 的组件的代码均可启动。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="5a3fe-112">可以在 <xref:System.ServiceProcess.ServiceInstaller> 类中设置 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性，以确定是应该手动还是自动启动服务。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="5a3fe-113">指定服务的启动方式</span><span class="sxs-lookup"><span data-stu-id="5a3fe-113">To specify how a service should start</span></span>  
  
1. <span data-ttu-id="5a3fe-114">在创建服务后为其添加必要的安装程序。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="5a3fe-115">有关详细信息，请参阅[如何：将安装程序添加到服务应用程序](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="5a3fe-116">在设计器中，单击正在使用的服务的服务安装程序。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3. <span data-ttu-id="5a3fe-117">在“属性”  窗口中，将 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性设置为以下之一：</span><span class="sxs-lookup"><span data-stu-id="5a3fe-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="5a3fe-118">安装服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-118">To have your service install</span></span>|<span data-ttu-id="5a3fe-119">设置此值</span><span class="sxs-lookup"><span data-stu-id="5a3fe-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="5a3fe-120">计算机重启时</span><span class="sxs-lookup"><span data-stu-id="5a3fe-120">When the computer is restarted</span></span>|<span data-ttu-id="5a3fe-121">**自动**</span><span class="sxs-lookup"><span data-stu-id="5a3fe-121">**Automatic**</span></span>|  
    |<span data-ttu-id="5a3fe-122">显式用户动作启动服务时</span><span class="sxs-lookup"><span data-stu-id="5a3fe-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="5a3fe-123">手动 </span><span class="sxs-lookup"><span data-stu-id="5a3fe-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="5a3fe-124">为防止服务完全启动，可以将 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性设置为“禁用”  。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="5a3fe-125">如果要多次重启服务器并希望通过阻止在服务器启动时通常会启动的服务来节省时间，则可以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5a3fe-126">安装服务后，可以更改这些属性和其他属性。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="5a3fe-127">可以通过多种方式启动将其 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 进程设置为“手动”  的服务 — 从“服务器资源管理器”、   “Windows 服务控制管理器”，或从代码均可启动。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="5a3fe-128">请务必注意，实际上，并非所有这些方法都在服务控制管理器  的上下文中启动服务；  服务器资源管理器和启动服务的编程方法实际上会操纵控制器。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="5a3fe-129">从“服务器资源管理器”手动启动服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-129">To manually start a service from Server Explorer</span></span>  
  
1. <span data-ttu-id="5a3fe-130">在“服务器资源管理器”  中，添加所需的服务器（如果尚未列出）。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="5a3fe-131">有关详细信息，请参阅“操作说明：访问和初始化服务器资源管理器/数据库资源管理器。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2. <span data-ttu-id="5a3fe-132">展开“服务”  节点，然后找到要启动的服务。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3. <span data-ttu-id="5a3fe-133">右键单击该服务的名称，然后单击“启动”  。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="5a3fe-134">从“服务控制管理器”手动启动服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-134">To manually start a service from Services Control Manager</span></span>  
  
1. <span data-ttu-id="5a3fe-135">执行以下操作之一，打开“服务控制管理器”  ：</span><span class="sxs-lookup"><span data-stu-id="5a3fe-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    - <span data-ttu-id="5a3fe-136">在 Windows XP 和 2000 Professional 中，右键单击桌面上的“我的电脑”  ，然后单击“管理”  。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="5a3fe-137">在出现的对话框中，展开“服务和应用程序”  节点。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="5a3fe-138">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5a3fe-138">\- or -</span></span>  
  
    - <span data-ttu-id="5a3fe-139">在 Windows Server 2003 和 Windows 2000 Server 中，单击“开始”  ，指向“程序”  ，单击“管理工具”  ，然后单击“服务”  。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5a3fe-140">在 Windows NT 4.0 版中，可以从“控制面板”  打开此对话框。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="5a3fe-141">现在应该可看到在窗口的“服务”  部分列出的服务。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2. <span data-ttu-id="5a3fe-142">从列表中选择你的服务，右键单击该服务，然后单击“启动”  。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="5a3fe-143">从代码手动启动服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-143">To manually start a service from code</span></span>  
  
1. <span data-ttu-id="5a3fe-144">创建 <xref:System.ServiceProcess.ServiceController> 类的实例，并将其配置为与要管理的服务进行交互。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2. <span data-ttu-id="5a3fe-145">调用 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法以启动该服务。</span><span class="sxs-lookup"><span data-stu-id="5a3fe-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3fe-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="5a3fe-146">See also</span></span>

- [<span data-ttu-id="5a3fe-147">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="5a3fe-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5a3fe-148">如何：创建 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="5a3fe-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="5a3fe-149">如何：将安装程序添加到服务应用程序</span><span class="sxs-lookup"><span data-stu-id="5a3fe-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
