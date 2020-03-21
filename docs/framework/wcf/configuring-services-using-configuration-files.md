---
title: 使用配置文件配置服务
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174792"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="ebe15-102">使用配置文件配置服务</span><span class="sxs-lookup"><span data-stu-id="ebe15-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="ebe15-103">使用配置文件配置 Windows 通信基础 （WCF） 服务使您能够灵活地在部署点提供终结点和服务行为数据，而不是在设计时提供。</span><span class="sxs-lookup"><span data-stu-id="ebe15-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="ebe15-104">本主题概述了当前可用的主要技术。</span><span class="sxs-lookup"><span data-stu-id="ebe15-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="ebe15-105">WCF 服务可使用 .NET 框架配置技术进行配置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="ebe15-106">最常见的情况是，XML 元素被添加到 Web.config 文件中，用于托管 WCF 服务的 Internet 信息服务 （IIS） 站点。</span><span class="sxs-lookup"><span data-stu-id="ebe15-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="ebe15-107">通过这些元素，可以逐台计算机更改详细信息，例如终结点地址（用于与服务进行通信的实际地址）。</span><span class="sxs-lookup"><span data-stu-id="ebe15-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="ebe15-108">此外，WCF 还包括几个系统提供的元素，允许您快速选择服务的最基本功能。</span><span class="sxs-lookup"><span data-stu-id="ebe15-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="ebe15-109">从 .NET 框架 4 开始，WCF 附带了一种新的默认配置模型，简化了 WCF 配置要求。</span><span class="sxs-lookup"><span data-stu-id="ebe15-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="ebe15-110">如果不为特定服务提供任何 WCF 配置，运行时将自动配置服务与一些标准终结点和默认绑定/行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="ebe15-111">实际上，写入配置是编程 WCF 应用程序的主要部分。</span><span class="sxs-lookup"><span data-stu-id="ebe15-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="ebe15-112">有关详细信息，请参阅[配置服务的绑定](configuring-bindings-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe15-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="ebe15-113">有关最常用的元素的列表，请参阅[系统提供的绑定](system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe15-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="ebe15-114">有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](simplified-configuration.md)和 [WCF 服务的简化配置](./samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe15-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ebe15-115">在部署并行方案（其中部署了服务的两个不同版本）时，必须指定配置文件中引用的程序集的部分名称。</span><span class="sxs-lookup"><span data-stu-id="ebe15-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="ebe15-116">这是因为配置文件将在服务的所有版本间共享，并可在不同版本的 .NET Framework 下运行。</span><span class="sxs-lookup"><span data-stu-id="ebe15-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="ebe15-117">System.Configuration：Web.config 和 App.config</span><span class="sxs-lookup"><span data-stu-id="ebe15-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="ebe15-118">WCF 使用 .NET 框架的系统.配置配置系统。</span><span class="sxs-lookup"><span data-stu-id="ebe15-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ebe15-119">在 Visual Studio 中配置服务时，请使用 Web.config 文件或 App.config 文件来指定设置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="ebe15-120">配置文件名称的选择由为服务选择的宿主环境确定。</span><span class="sxs-lookup"><span data-stu-id="ebe15-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="ebe15-121">如果正在使用 IIS 来承载服务，则使用 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="ebe15-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="ebe15-122">如果正在使用任何其他宿主环境，则使用 App.config 文件。</span><span class="sxs-lookup"><span data-stu-id="ebe15-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="ebe15-123">在 Visual Studio 中，名为 App.config 的文件用于创建最终配置文件。</span><span class="sxs-lookup"><span data-stu-id="ebe15-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="ebe15-124">实际用于配置的最终名称取决于程序集名称。</span><span class="sxs-lookup"><span data-stu-id="ebe15-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="ebe15-125">例如，名为“Cohowinery.exe”的程序集具有的最终配置文件名称为“Cohowinery.exe.config”。</span><span class="sxs-lookup"><span data-stu-id="ebe15-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="ebe15-126">但是，只需要修改 App.config 文件。</span><span class="sxs-lookup"><span data-stu-id="ebe15-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="ebe15-127">在编译时，对该文件所做的更改会自动应用于最终应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="ebe15-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="ebe15-128">在使用 App.config 文件的过程中，当应用程序启动并应用配置时，文件配置系统会将 App.config 文件与 Machine.config 文件的内容合并。</span><span class="sxs-lookup"><span data-stu-id="ebe15-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="ebe15-129">此机制允许在 Machine.config 文件中定义计算机范围的设置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="ebe15-130">可以使用 App.config 文件重写 Machine.config 文件的设置；也可以锁定 Machine.config 文件中的设置以应用它们。</span><span class="sxs-lookup"><span data-stu-id="ebe15-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="ebe15-131">对于 Web.config，配置系统会将应用程序目录之下的所有目录中的 Web.config 文件合并到要应用的配置中。</span><span class="sxs-lookup"><span data-stu-id="ebe15-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="ebe15-132">有关配置和设置优先级的详细信息，请参阅命名空间中<xref:System.Configuration>的主题。</span><span class="sxs-lookup"><span data-stu-id="ebe15-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="ebe15-133">配置文件的主要部分</span><span class="sxs-lookup"><span data-stu-id="ebe15-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="ebe15-134">配置文件中的主要部分包括以下元素。</span><span class="sxs-lookup"><span data-stu-id="ebe15-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="ebe15-135">绑定部分和行为部分是可选的，只在需要时才包括。</span><span class="sxs-lookup"><span data-stu-id="ebe15-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="ebe15-136">服务\<>元素</span><span class="sxs-lookup"><span data-stu-id="ebe15-136">The \<services> Element</span></span>  
 <span data-ttu-id="ebe15-137">`services` 元素包含应用程序承载的所有服务的规范。</span><span class="sxs-lookup"><span data-stu-id="ebe15-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="ebe15-138">从 .NET 框架 4 中的简化配置模型开始，本节是可选的。</span><span class="sxs-lookup"><span data-stu-id="ebe15-138">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [<span data-ttu-id="ebe15-139">\<服务></span><span class="sxs-lookup"><span data-stu-id="ebe15-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="ebe15-140">服务\<>元素</span><span class="sxs-lookup"><span data-stu-id="ebe15-140">The \<service> Element</span></span>  
 <span data-ttu-id="ebe15-141">每个服务都具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="ebe15-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="ebe15-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-142">`name`.</span></span> <span data-ttu-id="ebe15-143">指定提供服务协定的实现的类型。</span><span class="sxs-lookup"><span data-stu-id="ebe15-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="ebe15-144">这是完全限定名称，其中包含命名空间、句点和类型名称。</span><span class="sxs-lookup"><span data-stu-id="ebe15-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="ebe15-145">例如，`"MyNameSpace.myServiceType"`。</span><span class="sxs-lookup"><span data-stu-id="ebe15-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="ebe15-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="ebe15-147">指定一个在 `behavior` 元素中找到的 `behaviors` 元素的名称。</span><span class="sxs-lookup"><span data-stu-id="ebe15-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="ebe15-148">指定的行为控制操作，例如服务是否允许模拟。</span><span class="sxs-lookup"><span data-stu-id="ebe15-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="ebe15-149">如果它的值是空的，或者未提供任何 `behaviorConfiguration` ，则向服务中添加默认服务行为集。</span><span class="sxs-lookup"><span data-stu-id="ebe15-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="ebe15-150">\<服务></span><span class="sxs-lookup"><span data-stu-id="ebe15-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="ebe15-151">>\<元素的终结点</span><span class="sxs-lookup"><span data-stu-id="ebe15-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="ebe15-152">每个终结点都需要以下属性表示的地址、绑定和协定：</span><span class="sxs-lookup"><span data-stu-id="ebe15-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="ebe15-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-153">`address`.</span></span> <span data-ttu-id="ebe15-154">指定服务的统一资源标识符 (URI)，它可以是一个绝对地址，或是一个相对于服务基址给定的地址。</span><span class="sxs-lookup"><span data-stu-id="ebe15-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="ebe15-155">如果设置为空字符串，则指示在创建服务的 <xref:System.ServiceModel.ServiceHost> 时，终结点在指定的基址上可用。</span><span class="sxs-lookup"><span data-stu-id="ebe15-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="ebe15-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-156">`binding`.</span></span> <span data-ttu-id="ebe15-157">通常，指定一个类似 <xref:System.ServiceModel.WSHttpBinding>的系统提供的绑定，但也可以指定一个用户定义的绑定。</span><span class="sxs-lookup"><span data-stu-id="ebe15-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="ebe15-158">指定的绑定确定传输协议类型、安全和使用的编码，以及是否支持或启用可靠会话、事务或流。</span><span class="sxs-lookup"><span data-stu-id="ebe15-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="ebe15-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-159">`bindingConfiguration`.</span></span> <span data-ttu-id="ebe15-160">如果必须修改绑定的默认值，则可通过在 `binding` 元素中配置相应的 `bindings` 元素来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ebe15-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="ebe15-161">此属性应赋予与用于更改默认值的 `name` 元素的 `binding` 属性相同的值。</span><span class="sxs-lookup"><span data-stu-id="ebe15-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="ebe15-162">如果未提供任何名称，或者在绑定中未指定任何 `bindingConfiguration` ，则在终结点中使用绑定类型的默认绑定。</span><span class="sxs-lookup"><span data-stu-id="ebe15-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="ebe15-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="ebe15-163">`contract`.</span></span> <span data-ttu-id="ebe15-164">指定定义协定的接口。</span><span class="sxs-lookup"><span data-stu-id="ebe15-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="ebe15-165">这是在由 `name` 元素的 `service` 属性指定的公共语言运行库 (CLR) 类型中实现的接口。</span><span class="sxs-lookup"><span data-stu-id="ebe15-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="ebe15-166">\<端点></span><span class="sxs-lookup"><span data-stu-id="ebe15-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="ebe15-167">元素\<>绑定</span><span class="sxs-lookup"><span data-stu-id="ebe15-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="ebe15-168">`bindings` 元素包含可由任何服务中定义的任何终结点使用的所有绑定的规范。</span><span class="sxs-lookup"><span data-stu-id="ebe15-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="ebe15-169">\<绑定></span><span class="sxs-lookup"><span data-stu-id="ebe15-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="ebe15-170">绑定\<>元素</span><span class="sxs-lookup"><span data-stu-id="ebe15-170">The \<binding> Element</span></span>  
 <span data-ttu-id="ebe15-171">在 `binding` 元素中包含的 `bindings` 元素可以是系统提供的绑定之一（请参阅 [System-Provided Bindings](system-provided-bindings.md)），也可以是自定义绑定（请参阅 [Custom Bindings](./extending/custom-bindings.md)）。</span><span class="sxs-lookup"><span data-stu-id="ebe15-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="ebe15-172">`binding` 元素具有 `name` 属性，此属性将绑定与 `bindingConfiguration` 元素的 `endpoint` 属性中指定的终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="ebe15-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="ebe15-173">如果未指定任何名称，则该绑定对应于该绑定类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="ebe15-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="ebe15-174">有关配置服务和客户端的详细信息，请参阅[配置 WCF 服务](configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe15-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="ebe15-175">\<绑定></span><span class="sxs-lookup"><span data-stu-id="ebe15-175">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="ebe15-176">元素\<>行为</span><span class="sxs-lookup"><span data-stu-id="ebe15-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="ebe15-177">这是定义服务行为的 `behavior` 元素的容器元素。</span><span class="sxs-lookup"><span data-stu-id="ebe15-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="ebe15-178">\<行为></span><span class="sxs-lookup"><span data-stu-id="ebe15-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="ebe15-179">>\<元素的行为</span><span class="sxs-lookup"><span data-stu-id="ebe15-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="ebe15-180">每个`behavior`元素都由属性`name`标识，并提供系统提供的行为，如<>`throttling`或自定义行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="ebe15-181">如果未提供任何名称，则该行为元素对应于默认服务或终结点行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="ebe15-182">\<行为></span><span class="sxs-lookup"><span data-stu-id="ebe15-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="ebe15-183">如何使用绑定和行为配置</span><span class="sxs-lookup"><span data-stu-id="ebe15-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="ebe15-184">WCF 使使用配置中的参考系统轻松地在端点之间共享配置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="ebe15-185">与绑定相关的配置值在 `bindingConfiguration` 部分的 `<binding>` 元素中进行分组，而不是直接将配置值分配到终结点。</span><span class="sxs-lookup"><span data-stu-id="ebe15-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="ebe15-186">绑定配置是一组命名的绑定设置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="ebe15-187">然后，终结点可以通过名称来引用 `bindingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="ebe15-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ebe15-188">在 `name` 元素中设置 `bindingConfiguration` 的 `<binding>` 。</span><span class="sxs-lookup"><span data-stu-id="ebe15-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="ebe15-189">必须是`name`绑定类型范围内的唯一字符串 ，在这种情况下[，<基本\>HttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)，或引用默认绑定的空值。</span><span class="sxs-lookup"><span data-stu-id="ebe15-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="ebe15-190">通过将 `bindingConfiguration` 属性设置为此字符串，终结点链接到该配置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="ebe15-191">以相同方式实现 `behaviorConfiguration` ，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="ebe15-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ebe15-192">请注意，向服务中添加了默认服务行为集。</span><span class="sxs-lookup"><span data-stu-id="ebe15-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="ebe15-193">此系统允许终结点共享公共配置而不用重新定义设置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="ebe15-194">如果需要机器范围，请在"机器.config"中创建绑定或行为配置。配置设置在所有 App.config 文件中都可用。</span><span class="sxs-lookup"><span data-stu-id="ebe15-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="ebe15-195">通过 [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) 可以很方便地创建配置。</span><span class="sxs-lookup"><span data-stu-id="ebe15-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="ebe15-196">行为合并</span><span class="sxs-lookup"><span data-stu-id="ebe15-196">Behavior Merge</span></span>  
 <span data-ttu-id="ebe15-197">当您需要统一使用一组公共行为时，利用行为合并功能，可更加轻松地管理行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="ebe15-198">此功能允许您在配置层次结构的各个层上指定行为，并使服务能够从配置层次结构的多个层继承行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="ebe15-199">为了演示此功能的工作方式，假定您的 IIS 中包含以下虚拟目录布局：</span><span class="sxs-lookup"><span data-stu-id="ebe15-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="ebe15-200">您的`~\Web.config`文件包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="ebe15-200">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ebe15-201">具有一个位于 ~\Child\Web.config 并包含以下内容的子 Web.config：</span><span class="sxs-lookup"><span data-stu-id="ebe15-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ebe15-202">位于 ~\Child\Service.svc 的服务的行为如同该服务具有 serviceDebug 和 serviceMetadata 行为一样。</span><span class="sxs-lookup"><span data-stu-id="ebe15-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="ebe15-203">位于 ~\Service.svc 的服务只具有 serviceDebug 行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="ebe15-204">发生的情况是，名称相同的两个行为集合（此情况下为空字符串）将合并。</span><span class="sxs-lookup"><span data-stu-id="ebe15-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="ebe15-205">您还可以使用\<清除>标记来清除行为集合，并使用\<删除>标记从集合中删除单个行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="ebe15-206">例如，子服务中的以下两个配置结果只具有 serviceMetadata 行为：</span><span class="sxs-lookup"><span data-stu-id="ebe15-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ebe15-207">对无名称行为集合执行行为合并（如上所示），并对命名行为集合执行行为合并。</span><span class="sxs-lookup"><span data-stu-id="ebe15-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="ebe15-208">行为合并在 IIS 托管环境中工作，Web.config 文件与 root Web.config 文件和计算机分层合并。但它也在应用程序环境中工作，其中计算机.config 可以与 App.config 文件合并。</span><span class="sxs-lookup"><span data-stu-id="ebe15-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="ebe15-209">行为合并适用于配置中的终结点行为和服务行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="ebe15-210">如果子行为集合包含一个已显示在父行为集合中的行为，则子行为将重写父行为。</span><span class="sxs-lookup"><span data-stu-id="ebe15-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="ebe15-211">因此，如果父行为集合具有`<serviceMetadata httpGetEnabled="False" />`和子行为集合具有`<serviceMetadata httpGetEnabled="True" />`，则子行为将覆盖行为集合中的父行为，httpGetEnabled 将为"true"。</span><span class="sxs-lookup"><span data-stu-id="ebe15-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe15-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebe15-212">See also</span></span>

- [<span data-ttu-id="ebe15-213">简化配置</span><span class="sxs-lookup"><span data-stu-id="ebe15-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="ebe15-214">配置 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="ebe15-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="ebe15-215">\<服务></span><span class="sxs-lookup"><span data-stu-id="ebe15-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="ebe15-216">\<绑定></span><span class="sxs-lookup"><span data-stu-id="ebe15-216">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)
