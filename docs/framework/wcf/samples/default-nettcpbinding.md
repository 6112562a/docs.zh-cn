---
title: 默认 NetTcpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
ms.openlocfilehash: a96ff1b588bd86ee3c391ea37b7ca5724db5e650
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589880"
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="0b6b9-102">默认 NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="0b6b9-102">Default NetTcpBinding</span></span>
<span data-ttu-id="0b6b9-103">本示例演示 <xref:System.ServiceModel.NetTcpBinding> 绑定的用法。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="0b6b9-104">此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)实现计算器服务。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0b6b9-105">在本示例中，服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="0b6b9-106">客户端和服务都是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b6b9-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b6b9-108">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b6b9-109">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="0b6b9-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b6b9-110">如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b6b9-111">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="0b6b9-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="0b6b9-112">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0b6b9-113">中指定的绑定类型`binding`的属性[\<终结点 >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)元素，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="0b6b9-114">前面的示例演示如何配置终结点以使用具有默认设置的 `netTcpBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="0b6b9-115">如果要配置 `netTcpBinding` 绑定并更改它的一些设置，则必须定义绑定配置。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="0b6b9-116">终结点必须使用 `bindingConfiguration` 属性按名称来引用绑定配置。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="0b6b9-117">在本示例中，绑定配置的名称为 `Binding1` 并按下面的示例配置所示进行定义。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="0b6b9-118">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0b6b9-119">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b6b9-120">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="0b6b9-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0b6b9-121">使用以下命令安装 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="0b6b9-122">请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="0b6b9-123">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="0b6b9-124">若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b6b9-125">由于该服务器是自承载的，因此必须在客户端的 App.config 文件中指定一个标识才能用跨计算机配置来运行该示例。</span><span class="sxs-lookup"><span data-stu-id="0b6b9-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name=""  
          address="net.tcp://servername:9000/servicemodelsamples/service"   
          binding="netTcpBinding"   
          contract="Microsoft.ServiceModel.Samples.ICalculator">  
            <identity>  
              <userPrincipalName value = "user_name@service_domain"/>  
            </identity>  
      </endpoint>  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0b6b9-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="0b6b9-126">See also</span></span>
