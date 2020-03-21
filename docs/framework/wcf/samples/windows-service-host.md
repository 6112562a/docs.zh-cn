---
title: Windows 服务主机
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143520"
---
# <a name="windows-service-host"></a><span data-ttu-id="0b780-102">Windows 服务主机</span><span class="sxs-lookup"><span data-stu-id="0b780-102">Windows Service Host</span></span>
<span data-ttu-id="0b780-103">此示例演示托管 Windows 服务中托管的 Windows 通信基础 （WCF） 服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-103">This sample demonstrates a Windows Communication Foundation (WCF) service hosted in a managed Windows Service.</span></span> <span data-ttu-id="0b780-104">Windows 服务使用 **"控制面板**"中的服务小程序进行控制，并可配置为在系统重新启动后自动启动。</span><span class="sxs-lookup"><span data-stu-id="0b780-104">Windows Services are controlled using the Services applet in **Control Panel** and can be configured to start up automatically after a system reboot.</span></span> <span data-ttu-id="0b780-105">此示例包含一个客户端程序和一个 Windows 服务程序。</span><span class="sxs-lookup"><span data-stu-id="0b780-105">The sample consists of a client program and an Windows Service program.</span></span> <span data-ttu-id="0b780-106">服务作为一个 .exe 程序实现，并包含其自己的主机代码。</span><span class="sxs-lookup"><span data-stu-id="0b780-106">The service is implemented as an .exe program and contains its own hosting code.</span></span> <span data-ttu-id="0b780-107">在其他承载环境（如 Windows 进程激活服务 (WAS) 或 Internet Information Services (IIS)）中，你没有必要编写承载代码。</span><span class="sxs-lookup"><span data-stu-id="0b780-107">In other hosting environments, such as Windows Process Activation Services (WAS) or Internet Information Services (IIS), it is not necessary for you to write hosting code.</span></span>

> [!NOTE]
> <span data-ttu-id="0b780-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="0b780-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b780-109">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="0b780-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0b780-110">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="0b780-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0b780-111">如果此目录不存在，请转到[Windows 通信基础 （WCF） 和 Windows 工作流基础 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下载[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基础 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="0b780-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b780-112">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="0b780-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 <span data-ttu-id="0b780-113">生成此服务之后，必须像任何其他 Windows 服务一样使用 Installutil.exe 实用工具安装此服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-113">After building this service, it must be installed with the Installutil.exe utility like any other Windows Service.</span></span> <span data-ttu-id="0b780-114">如果要对此服务进行更改，必须首先使用 `installutil /u` 将其卸载。</span><span class="sxs-lookup"><span data-stu-id="0b780-114">If you are going to make changes to the service, you must first uninstall it with `installutil /u`.</span></span> <span data-ttu-id="0b780-115">此示例中随附的 Setup.bat 和 Cleanup.bat 文件是用于安装和启动 Windows 服务的命令，还可用于关闭和卸载 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-115">The Setup.bat and Cleanup.bat files included in this sample are the commands to install and start up the Windows Service, and to shut down and uninstall the Windows Service.</span></span> <span data-ttu-id="0b780-116">仅当 Windows 服务正在运行时，WCF 服务才能响应客户端。</span><span class="sxs-lookup"><span data-stu-id="0b780-116">The WCF service can only respond to clients if the Windows Service is running.</span></span> <span data-ttu-id="0b780-117">如果使用 **"控制面板**"中的服务小程序停止 Windows 服务并运行客户端，则客户端尝试<xref:System.ServiceModel.EndpointNotFoundException>访问该服务时将发生异常。</span><span class="sxs-lookup"><span data-stu-id="0b780-117">If you stop the Windows Service by using the Services applet from **Control Panel** and run the client, a <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="0b780-118">如果重新启动 Windows 服务并重新运行客户端，通信将成功。</span><span class="sxs-lookup"><span data-stu-id="0b780-118">If you restart the Windows Service and rerun the client, communication succeeds.</span></span>  
  
 <span data-ttu-id="0b780-119">服务代码包括安装程序类、实现 I计算器协定的 WCF 服务实现类以及充当运行时主机的 Windows 服务类。</span><span class="sxs-lookup"><span data-stu-id="0b780-119">The service code includes an installer class, a WCF service implementation class which implements the ICalculator contract, and a Windows Service class that acts as the run-time host.</span></span> <span data-ttu-id="0b780-120">安装程序类继承自 <xref:System.Configuration.Install.Installer>，允许通过 Installutil.exe 工具将程序安装为 NT 服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-120">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as an NT service by the Installutil.exe tool.</span></span> <span data-ttu-id="0b780-121">服务实现类`WcfCalculatorService`是实现基本服务协定的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-121">The service implementation class, `WcfCalculatorService`, is an WCF service that implements a basic service contract.</span></span> <span data-ttu-id="0b780-122">此 WCF 服务托管在称为`WindowsCalculatorService`的 Windows 服务类中。</span><span class="sxs-lookup"><span data-stu-id="0b780-122">This WCF service is hosted inside a Windows Service class called `WindowsCalculatorService`.</span></span> <span data-ttu-id="0b780-123">为了符合作为 Windows 服务的要求，该类从 <xref:System.ServiceProcess.ServiceBase> 继承并实现 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 和 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法。</span><span class="sxs-lookup"><span data-stu-id="0b780-123">To qualify as a Windows Service, the class inherits from <xref:System.ServiceProcess.ServiceBase> and implements the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> and <xref:System.ServiceProcess.ServiceBase.OnStop> methods.</span></span> <span data-ttu-id="0b780-124">在 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 中，为 <xref:System.ServiceModel.ServiceHost> 类型创建并打开了 `WcfCalculatorService` 对象。</span><span class="sxs-lookup"><span data-stu-id="0b780-124">In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, a <xref:System.ServiceModel.ServiceHost> object is created for the `WcfCalculatorService` type and opened.</span></span> <span data-ttu-id="0b780-125">在 <xref:System.ServiceProcess.ServiceBase.OnStop> 中，通过调用 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 对象的 <xref:System.ServiceModel.ServiceHost> 方法关闭了 ServiceHost。</span><span class="sxs-lookup"><span data-stu-id="0b780-125">In <xref:System.ServiceProcess.ServiceBase.OnStop>, the ServiceHost is closed by calling the <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> method of the <xref:System.ServiceModel.ServiceHost> object.</span></span> <span data-ttu-id="0b780-126">主机的基本地址使用[\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)元素进行配置，该元素是[\<基地址>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)的子元素，它是[\<主机>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)元素的子项，该元素是[\<服务>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="0b780-126">The host's base address is configured using the [\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, which is a child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), which is a child of the [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, which is a child of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element.</span></span>  
  
 <span data-ttu-id="0b780-127">定义的终结点使用基本地址和[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="0b780-127">The endpoint that is defined uses the base address and a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="0b780-128">下面的示例演示了基本地址的配置以及公开 CalculatorService 的终结点。</span><span class="sxs-lookup"><span data-stu-id="0b780-128">The following sample shows the configuration of the base address as well as the endpoint that exposes the CalculatorService.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 <span data-ttu-id="0b780-129">运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="0b780-129">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0b780-130">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="0b780-130">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b780-131">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="0b780-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0b780-132">确保已为 Windows[通信基础示例执行一次性设置过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b780-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0b780-133">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="0b780-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0b780-134">构建解决方案后，从提升的 Visual Studio 2012 命令提示符运行安装程序.bat，使用 Installutil.exe 工具安装 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="0b780-134">After the solution has been built, run Setup.bat from an elevated Visual Studio 2012 command prompt to install the Windows service using the Installutil.exe tool.</span></span> <span data-ttu-id="0b780-135">该服务应出现在“服务”中。</span><span class="sxs-lookup"><span data-stu-id="0b780-135">The service should appear in Services.</span></span>  
  
4. <span data-ttu-id="0b780-136">要在单计算机或跨计算机配置中运行示例，请按照[运行 Windows 通信基础示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)说明操作。</span><span class="sxs-lookup"><span data-stu-id="0b780-136">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b780-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b780-137">See also</span></span>

- <span data-ttu-id="0b780-138">[AppFabric 承载和持久性示例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0b780-138">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
