---
title: 为 Windows Communication Foundation 服务配置绑定
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174818"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="05862-102">为 Windows Communication Foundation 服务配置绑定</span><span class="sxs-lookup"><span data-stu-id="05862-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="05862-103">创建应用程序时，您经常需要将一些决策交给管理员在部署应用程序后制定。</span><span class="sxs-lookup"><span data-stu-id="05862-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="05862-104">例如，通常没有办法提前知道服务地址或统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="05862-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="05862-105">最好允许管理员在创建服务后指定地址，而不是对地址进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="05862-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="05862-106">这种灵活性是通过配置实现的。</span><span class="sxs-lookup"><span data-stu-id="05862-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05862-107">将[服务模型元数据实用程序工具 （Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)与`/config`交换机一起使用，快速创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="05862-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="05862-108">主要部分</span><span class="sxs-lookup"><span data-stu-id="05862-108">Major Sections</span></span>  
 <span data-ttu-id="05862-109">Windows 通信基础 （WCF） 配置方案包括以下三个主要部分`serviceModel` `bindings`（、`services`和 ）：</span><span class="sxs-lookup"><span data-stu-id="05862-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="05862-110">ServiceModel 元素</span><span class="sxs-lookup"><span data-stu-id="05862-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="05862-111">可以使用元素`system.ServiceModel`绑定的部分配置具有一个或多个终结点的服务类型以及服务的设置。</span><span class="sxs-lookup"><span data-stu-id="05862-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="05862-112">然后，可以为每个终结点配置地址、协定以及绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="05862-113">有关终结点的详细信息，请参阅[终结点创建概述](endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="05862-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="05862-114">如果未指定任何终结点，则运行时添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="05862-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="05862-115">有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](simplified-configuration.md)和 [WCF 服务的简化配置](./samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="05862-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="05862-116">绑定指定传输（HTTP、TCP、管道、消息队列）和协议（安全性、可靠性、事务流）。绑定由绑定元素组成，其中的每个元素都指定终结点与世界的通信方式的一个方面。</span><span class="sxs-lookup"><span data-stu-id="05862-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="05862-117">例如，指定[\<基本 HttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)元素指示使用 HTTP 作为终结点的传输。</span><span class="sxs-lookup"><span data-stu-id="05862-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="05862-118">这用于在使用此终结点的服务打开时在运行时连接终结点。</span><span class="sxs-lookup"><span data-stu-id="05862-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="05862-119">有两种绑定：预定义绑定和自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="05862-120">预定义绑定包含在常见方案中使用的元素的有用组合。</span><span class="sxs-lookup"><span data-stu-id="05862-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="05862-121">有关 WCF 提供的预定义绑定类型的列表，请参阅[系统提供的绑定](system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="05862-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="05862-122">如果没有任何预定义绑定集合具有服务应用程序所需的功能的正确组合，那么你可以构造自定义绑定来满足应用程序的需求。</span><span class="sxs-lookup"><span data-stu-id="05862-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="05862-123">有关自定义绑定的详细信息，请参阅[\<自定义绑定>](../configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="05862-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="05862-124">以下四个示例说明了用于设置 WCF 服务的最常见绑定配置。</span><span class="sxs-lookup"><span data-stu-id="05862-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="05862-125">指定终结点以使用绑定类型</span><span class="sxs-lookup"><span data-stu-id="05862-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="05862-126">第一个示例说明如何指定一个配置了地址、协定和绑定的终结点。</span><span class="sxs-lookup"><span data-stu-id="05862-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="05862-127">在本示例中，`name` 属性表示使用该配置的服务类型。</span><span class="sxs-lookup"><span data-stu-id="05862-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="05862-128">当您用 `HelloWorld` 协定通过代码中创建服务时，它将以示例配置中定义的所有终结点进行初始化。</span><span class="sxs-lookup"><span data-stu-id="05862-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="05862-129">如果程序集仅实现一个服务协定，则可以`name`省略该属性，因为服务使用唯一可用类型。</span><span class="sxs-lookup"><span data-stu-id="05862-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="05862-130">该属性采用字符串，该字符串必须遵循以下格式：`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="05862-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="05862-131">`address` 属性指定其他终结点用于与该服务通信的 URI。</span><span class="sxs-lookup"><span data-stu-id="05862-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="05862-132">该 URI 可以是绝对路径，也可以是相对路径。</span><span class="sxs-lookup"><span data-stu-id="05862-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="05862-133">如果提供的是相对地址，则需要主机提供适合于绑定中所使用的传输方案的基址。</span><span class="sxs-lookup"><span data-stu-id="05862-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="05862-134">如果未配置地址，则假定基址为该终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="05862-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="05862-135">`contract` 属性指定该终结点所公开的协定。</span><span class="sxs-lookup"><span data-stu-id="05862-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="05862-136">服务实现类型必须实现该协定类型。</span><span class="sxs-lookup"><span data-stu-id="05862-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="05862-137">如果服务实现所实现的是单个协定类型，则可以省略此属性。</span><span class="sxs-lookup"><span data-stu-id="05862-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="05862-138">`binding` 属性选择要用于此特定终结点的预定义或自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="05862-139">不显式选择绑定的终结点使用默认绑定选择，即 `BasicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="05862-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="05862-140">修改预定义绑定</span><span class="sxs-lookup"><span data-stu-id="05862-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="05862-141">在下面的示例中，修改了预定义绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="05862-142">然后可以将该绑定用于配置服务中的任意终结点。</span><span class="sxs-lookup"><span data-stu-id="05862-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="05862-143">可通过将 <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 值设置为 1 秒的方式来修改绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="05862-144">请注意，该属性返回一个 <xref:System.TimeSpan> 对象。</span><span class="sxs-lookup"><span data-stu-id="05862-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="05862-145">在绑定部分中可以找到该更改的绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="05862-146">现在，通过在 `binding` 元素中设置 `endpoint` 特性，可以在创建任何终结点时使用该更改的绑定。</span><span class="sxs-lookup"><span data-stu-id="05862-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05862-147">如果为该绑定指定了特定名称，则服务终结点中指定的 `bindingConfiguration` 必须与其相匹配。</span><span class="sxs-lookup"><span data-stu-id="05862-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="05862-148">配置要应用于服务的行为</span><span class="sxs-lookup"><span data-stu-id="05862-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="05862-149">在下面的示例中，为该服务类型配置了一个特定的行为。</span><span class="sxs-lookup"><span data-stu-id="05862-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="05862-150">该`ServiceMetadataBehavior`元素用于启用[ServiceModel 元数据实用程序工具 （Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)查询服务并从元数据生成 Web 服务描述语言 （WSDL） 文档。</span><span class="sxs-lookup"><span data-stu-id="05862-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05862-151">如果为该行为指定了特定名称，则服务或终结点部分中指定的 `behaviorConfiguration` 必须与其相匹配。</span><span class="sxs-lookup"><span data-stu-id="05862-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />
    </behavior>  
</behaviors>  
<services>  
    <service
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="05862-152">上面的配置使客户端可以调用并获取“HelloWorld”类型的服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="05862-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="05862-153">使用不同的绑定值指定具有两个终结点的服务</span><span class="sxs-lookup"><span data-stu-id="05862-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="05862-154">这是最后一个示例，在本示例中，为 `HelloWorld` 服务类型配置了两个终结点。</span><span class="sxs-lookup"><span data-stu-id="05862-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="05862-155">每个终结点使用相同绑定类型的`bindingConfiguration`不同自定义属性（每个终结点都修改`basicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="05862-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="05862-156">通过添加 `protocolMapping` 部分并按下面的示例所示配置绑定，可以使用默认配置获得相同的行为。</span><span class="sxs-lookup"><span data-stu-id="05862-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05862-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05862-157">See also</span></span>

- [<span data-ttu-id="05862-158">简化配置</span><span class="sxs-lookup"><span data-stu-id="05862-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="05862-159">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="05862-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="05862-160">终结点创建概述</span><span class="sxs-lookup"><span data-stu-id="05862-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="05862-161">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="05862-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
