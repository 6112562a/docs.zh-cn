---
title: 简化配置
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 3bed6fe961712c976d5e1446ace43e7073036697
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423708"
---
# <a name="simplified-configuration"></a><span data-ttu-id="47264-102">简化配置</span><span class="sxs-lookup"><span data-stu-id="47264-102">Simplified Configuration</span></span>
<span data-ttu-id="47264-103">配置 Windows Communication Foundation （WCF）服务可以是一种复杂的任务。</span><span class="sxs-lookup"><span data-stu-id="47264-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="47264-104">该任务涉及多个不同选项，并且有时会很难确定需要哪些设置。</span><span class="sxs-lookup"><span data-stu-id="47264-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="47264-105">虽然配置文件提高了 WCF 服务的灵活性，但是它们也是很难找到问题的源。</span><span class="sxs-lookup"><span data-stu-id="47264-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="47264-106">解决了这些问题，并向用户提供了一种减小服务配置大小和降低复杂性的方法。</span><span class="sxs-lookup"><span data-stu-id="47264-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="47264-107">简化配置</span><span class="sxs-lookup"><span data-stu-id="47264-107">Simplified Configuration</span></span>  
 <span data-ttu-id="47264-108">在 WCF 服务配置文件中，< `system.serviceModel` > 部分包含每个托管服务的 < `service` > 元素。</span><span class="sxs-lookup"><span data-stu-id="47264-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="47264-109">`service`> 元素包含 <`endpoint`元素的集合，这些元素指定为每项服务公开的终结点以及一组服务行为（可选）。</span><span class="sxs-lookup"><span data-stu-id="47264-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="47264-110"><`endpoint`> 元素指定终结点公开的地址、绑定和协定，以及绑定配置和终结点行为（可选）。</span><span class="sxs-lookup"><span data-stu-id="47264-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="47264-111">"<`system.serviceModel`>" 部分还包含 <`behaviors`元素，可用于指定服务或终结点行为。</span><span class="sxs-lookup"><span data-stu-id="47264-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="47264-112">下面的示例演示配置文件的 < `system.serviceModel` > 部分。</span><span class="sxs-lookup"><span data-stu-id="47264-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="47264-113">通过 <`service`> 元素删除要求，使 WCF 服务配置更容易。</span><span class="sxs-lookup"><span data-stu-id="47264-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="47264-114">如果未 < `service` > 部分添加或在 < `service` > 部分中添加任何终结点，并且服务未以编程方式定义任何终结点，则会将一组默认终结点自动添加到服务中，每个服务基址对应一个终结点。和服务实现的每个协定。</span><span class="sxs-lookup"><span data-stu-id="47264-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="47264-115">在上述每个终结点中，终结点地址与基址相对应，绑定由基址方案确定，协定即为服务实现的协定。</span><span class="sxs-lookup"><span data-stu-id="47264-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="47264-116">如果你不需要指定任何终结点或服务行为，或者不需要更改任何绑定设置，则完全不必指定服务配置文件。</span><span class="sxs-lookup"><span data-stu-id="47264-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="47264-117">如果服务实现了两个协定，并且主机同时启用了 HTTP 和 TCP 传输，服务主机将创建四个默认终结点，使用每个传输的每一协定各对应一个终结点。</span><span class="sxs-lookup"><span data-stu-id="47264-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="47264-118">若要创建默认终结点，服务主机必须了解要使用的绑定。</span><span class="sxs-lookup"><span data-stu-id="47264-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="47264-119">这些设置在 "< `system.serviceModel` >" 部分的 < `protocolMappings` > "部分中指定。</span><span class="sxs-lookup"><span data-stu-id="47264-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="47264-120">"<`protocolMappings`>" 部分包含映射到绑定类型的传输协议方案的列表。</span><span class="sxs-lookup"><span data-stu-id="47264-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="47264-121">服务主机使用传递到它的基址来确定要使用的绑定。</span><span class="sxs-lookup"><span data-stu-id="47264-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="47264-122">下面的示例使用 < `protocolMappings` > 元素。</span><span class="sxs-lookup"><span data-stu-id="47264-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="47264-123">更改默认配置元素（如绑定或行为）可能会影响在配置层次结构的较低级别中定义的服务，因为这些服务可能使用这些默认绑定和行为。</span><span class="sxs-lookup"><span data-stu-id="47264-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="47264-124">因而，更改默认绑定和行为的任何人员都需要注意，这些更改可能会影响层次结构中的其他服务。</span><span class="sxs-lookup"><span data-stu-id="47264-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47264-125">承载于 Internet 信息服务 (IIS) 或 Windows 进程激活服务 (WAS) 下的服务使用虚拟目录作为其基址。</span><span class="sxs-lookup"><span data-stu-id="47264-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="47264-126">在上一示例中，基址以“http”方案开头的终结点使用 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="47264-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="47264-127">基址以“net.tcp”方案开头的终结点使用 <xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="47264-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="47264-128">你可以在本地 App.config 或 Web.config 文件中重写相应设置。</span><span class="sxs-lookup"><span data-stu-id="47264-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="47264-129">"<`protocolMappings`>" 部分中的每个元素必须指定方案和绑定。</span><span class="sxs-lookup"><span data-stu-id="47264-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="47264-130">还可以指定一个 `bindingConfiguration` 属性，该属性在配置文件的 < `bindings` > 部分中指定绑定配置。</span><span class="sxs-lookup"><span data-stu-id="47264-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="47264-131">如果未指定 `bindingConfiguration`，则使用相应绑定类型的匿名绑定配置。</span><span class="sxs-lookup"><span data-stu-id="47264-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="47264-132">使用匿名 < 为默认终结点配置服务行为 `behavior` < `serviceBehaviors` > 部分中 > 部分。</span><span class="sxs-lookup"><span data-stu-id="47264-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="47264-133">`serviceBehaviors`> 中的任何未命名 <`behavior`> 元素用于配置服务行为。</span><span class="sxs-lookup"><span data-stu-id="47264-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="47264-134">例如，下面的配置文件对主机中的所有服务启用服务元数据发布。</span><span class="sxs-lookup"><span data-stu-id="47264-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="47264-135">终结点行为是使用匿名 < `behavior` > < `serviceBehaviors` > 部分内的节来配置的。</span><span class="sxs-lookup"><span data-stu-id="47264-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="47264-136">下面示例中的配置文件使用简化配置模型，它等效于本主题开头的配置文件。</span><span class="sxs-lookup"><span data-stu-id="47264-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> <span data-ttu-id="47264-137">此功能只与 WCF 服务配置相关，与客户端配置无关。</span><span class="sxs-lookup"><span data-stu-id="47264-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="47264-138">大多数时候，使用 svcutil.exe 之类的工具或从 Visual Studio 添加服务引用将生成 WCF 客户端配置。</span><span class="sxs-lookup"><span data-stu-id="47264-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="47264-139">如果要手动配置 WCF 客户端，则需要将 \<client > 元素添加到配置中，并指定希望调用的任何终结点。</span><span class="sxs-lookup"><span data-stu-id="47264-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47264-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="47264-140">See also</span></span>

- [<span data-ttu-id="47264-141">使用配置文件配置服务</span><span class="sxs-lookup"><span data-stu-id="47264-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="47264-142">配置服务绑定</span><span class="sxs-lookup"><span data-stu-id="47264-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="47264-143">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="47264-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="47264-144">配置服务</span><span class="sxs-lookup"><span data-stu-id="47264-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="47264-145">配置 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="47264-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="47264-146">在代码中配置 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="47264-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
