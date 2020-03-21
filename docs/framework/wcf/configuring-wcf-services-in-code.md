---
title: 在代码中配置 WCF 服务
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174805"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="e1c4f-102">在代码中配置 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="e1c4f-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="e1c4f-103">Windows 通信基础 （WCF） 允许开发人员使用配置文件或代码配置服务。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="e1c4f-104">当部署之后需要对服务进行配置时，配置文件十分有用。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="e1c4f-105">在使用配置文件时，IT 专业人员只需要更新配置文件，无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="e1c4f-106">不过，配置文件可能十分复杂，难以维护。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="e1c4f-107">不支持对配置文件进行调试，并且将按名称来引用配置元素，这使得配置文件的创作易于出错且较为困难。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="e1c4f-108">WCF 还允许您在代码中配置服务。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="e1c4f-109">在早期版本的 WCF（4.0 和更早版本）中，在自托管方案中配置服务很容易，<xref:System.ServiceModel.ServiceHost>该类允许您在调用 ServiceHost.Open 之前配置终结点和行为。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="e1c4f-110">但是，在 Web 承载方案中，你不具备针对 <xref:System.ServiceModel.ServiceHost> 类的直接访问权限。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="e1c4f-111">若要配置 Web 承载的服务，你需要创建 `System.ServiceModel.ServiceHostFactory`，后者会创建 <xref:System.ServiceModel.Activation.ServiceHostFactory> 并执行任何所需的配置。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="e1c4f-112">从 .NET 4.5 开始，WCF 提供了一种更简单的方法来在代码中配置自托管服务和 Web 托管服务。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="e1c4f-113">Configure 方法</span><span class="sxs-lookup"><span data-stu-id="e1c4f-113">The Configure method</span></span>  
 <span data-ttu-id="e1c4f-114">只需在您的服务实现类中使用以下签名定义名为 `Configure` 的公共静态方法：</span><span class="sxs-lookup"><span data-stu-id="e1c4f-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="e1c4f-115">Configure 方法采用 <xref:System.ServiceModel.ServiceConfiguration> 实例，使开发者可以添加终结点和行为。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="e1c4f-116">在打开服务主机之前，WCF 会调用此方法。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="e1c4f-117">定义后，将忽略 app.config 或 web.config 文件中指定的任何服务配置设置。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="e1c4f-118">下面的代码段阐释如何定义 `Configure` 方法和添加服务终结点、终结点行为以及服务行为：</span><span class="sxs-lookup"><span data-stu-id="e1c4f-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="e1c4f-119">要为服务启用协议（如 https），可以显式添加使用协议的终结点，也可以通过调用 ServiceConfiguration.EnableProtocol(Binding) 自动添加终结点，这样可为与协议兼容的每个基址和定义的每个服务协定添加终结点。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="e1c4f-120">下面的代码演示如何使用 ServiceConfiguration.EnableProtocol 方法：</span><span class="sxs-lookup"><span data-stu-id="e1c4f-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1
{
    public string GetData(int value);
    public static void Configure(ServiceConfiguration config)
    {
        // Enable "Add Service Reference" support
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });
       // set up support for http, https, net.tcp, net.pipe
       config.EnableProtocol(new BasicHttpBinding());
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 <span data-ttu-id="e1c4f-121">仅当未以编程方式`protocolMappings`将应用程序终结点添加到中时，才会使用<>部分中的<xref:System.ServiceModel.ServiceConfiguration>设置。您可以通过调用<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>然后更改设置，从默认应用程序配置文件中选择加载服务配置。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="e1c4f-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> 类还允许您从集中式配置加载配置。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="e1c4f-123">下面的代码演示如何实现这一点：</span><span class="sxs-lookup"><span data-stu-id="e1c4f-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1
{
    public void DoWork();
    public static void Configure(ServiceConfiguration config)
    {
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));
    }
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="e1c4f-124">请注意，<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>忽略<><>`host``service``system.serviceModel`标记中<>设置。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="e1c4f-125">从概念上讲`host`，<>是关于主机配置的，而不是服务配置，并且在"配置"方法执行之前加载它。</span><span class="sxs-lookup"><span data-stu-id="e1c4f-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c4f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1c4f-126">See also</span></span>

- [<span data-ttu-id="e1c4f-127">使用配置文件配置服务</span><span class="sxs-lookup"><span data-stu-id="e1c4f-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="e1c4f-128">配置客户端行为</span><span class="sxs-lookup"><span data-stu-id="e1c4f-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="e1c4f-129">简化配置</span><span class="sxs-lookup"><span data-stu-id="e1c4f-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="e1c4f-130">配置</span><span class="sxs-lookup"><span data-stu-id="e1c4f-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="e1c4f-131">IIS 和 WAS 中的基于配置的激活</span><span class="sxs-lookup"><span data-stu-id="e1c4f-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="e1c4f-132">配置和元数据支持</span><span class="sxs-lookup"><span data-stu-id="e1c4f-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="e1c4f-133">配置</span><span class="sxs-lookup"><span data-stu-id="e1c4f-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="e1c4f-134">如何：在配置中指定服务绑定</span><span class="sxs-lookup"><span data-stu-id="e1c4f-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="e1c4f-135">如何：在配置中创建服务终结点</span><span class="sxs-lookup"><span data-stu-id="e1c4f-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="e1c4f-136">如何：使用配置文件发布服务的元数据</span><span class="sxs-lookup"><span data-stu-id="e1c4f-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e1c4f-137">如何：在配置中指定客户端绑定</span><span class="sxs-lookup"><span data-stu-id="e1c4f-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
