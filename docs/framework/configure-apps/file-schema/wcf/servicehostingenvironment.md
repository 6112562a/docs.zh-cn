---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: b81c9f3c4260f415f057cd74b6f113d88f635978
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936290"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="a360e-101">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="a360e-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="a360e-102">此元素定义服务主机环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="a360e-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="a360e-103">如果此元素为空，则使用默认类型。</span><span class="sxs-lookup"><span data-stu-id="a360e-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="a360e-104">此元素只能在应用程序或计算机级别的配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="a360e-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="a360e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a360e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a360e-106">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="a360e-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a360e-107">语法</span><span class="sxs-lookup"><span data-stu-id="a360e-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a360e-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a360e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a360e-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a360e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a360e-110">特性</span><span class="sxs-lookup"><span data-stu-id="a360e-110">Attributes</span></span>  
  
|<span data-ttu-id="a360e-111">特性</span><span class="sxs-lookup"><span data-stu-id="a360e-111">Attribute</span></span>|<span data-ttu-id="a360e-112">描述</span><span class="sxs-lookup"><span data-stu-id="a360e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a360e-113">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="a360e-113">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="a360e-114">一个布尔值，指示是否已为当前应用程序启用了 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="a360e-114">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="a360e-115">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="a360e-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a360e-116">如果此特性设置为`true`, 则对 Windows Communication Foundation (WCF) 服务的请求将流经 ASP.NET HTTP 管道, 并且禁止通过非 HTTP 协议进行通信。</span><span class="sxs-lookup"><span data-stu-id="a360e-116">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="a360e-117">有关详细信息, 请参阅[WCF 服务和 ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="a360e-117">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="a360e-118">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="a360e-118">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="a360e-119">一个整数, 指定在可以激活 WCF 服务之前, 系统应提供的最小可用内存量。</span><span class="sxs-lookup"><span data-stu-id="a360e-119">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="a360e-120">注意：<xref:System.Security.SecurityException>如果在 WCF 服务的 web.config 文件中将此属性和部分信任一起指定, 则会在运行服务时生成。</span><span class="sxs-lookup"><span data-stu-id="a360e-120">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="a360e-121">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="a360e-121">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="a360e-122">一个布尔值，指定是否对每个站点启用多个 IIS 绑定。</span><span class="sxs-lookup"><span data-stu-id="a360e-122">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="a360e-123">IIS 由网站组成，这些网站是包含虚拟目录的虚拟应用程序的容器。</span><span class="sxs-lookup"><span data-stu-id="a360e-123">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="a360e-124">可通过一个或多个 IIS 绑定访问站点上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a360e-124">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="a360e-125">一个 IIS 绑定提供两条信息：绑定协议和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="a360e-125">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="a360e-126">绑定协议定义进行通信所依据的方案，而绑定信息是用于访问站点的信息。</span><span class="sxs-lookup"><span data-stu-id="a360e-126">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="a360e-127">绑定协议的一个示例可以是 HTTP，而绑定信息可包含 IP 地址、端口、主机标头等。</span><span class="sxs-lookup"><span data-stu-id="a360e-127">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="a360e-128">IIS 支持一个站点指定多个 IIS 绑定，这会导致一个方案有多个基址。</span><span class="sxs-lookup"><span data-stu-id="a360e-128">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="a360e-129">但是, 在站点下承载的 Windows Communication Foundation (WCF) 服务只允许绑定到每个方案的一个 baseAddress。</span><span class="sxs-lookup"><span data-stu-id="a360e-129">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="a360e-130">若要为一个 Windows Communication Foundation (WCF) 服务的每个站点启用多个 IIS 绑定, `true`请将此特性设置为。</span><span class="sxs-lookup"><span data-stu-id="a360e-130">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="a360e-131">请注意，仅对 HTTP 协议支持多个站点绑定。</span><span class="sxs-lookup"><span data-stu-id="a360e-131">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="a360e-132">配置文件中的终结点地址需要是一个完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="a360e-132">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a360e-133">子元素</span><span class="sxs-lookup"><span data-stu-id="a360e-133">Child Elements</span></span>  
  
|<span data-ttu-id="a360e-134">元素</span><span class="sxs-lookup"><span data-stu-id="a360e-134">Element</span></span>|<span data-ttu-id="a360e-135">描述</span><span class="sxs-lookup"><span data-stu-id="a360e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a360e-136">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="a360e-136">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="a360e-137">一个配置元素的集合，这些元素指定服务主机所使用的基址的前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="a360e-137">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="a360e-138">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="a360e-138">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="a360e-139">一个描述激活设置的配置节。</span><span class="sxs-lookup"><span data-stu-id="a360e-139">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="a360e-140">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="a360e-140">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="a360e-141">一个配置元素的集合，这些元素标识特定传输的类型。</span><span class="sxs-lookup"><span data-stu-id="a360e-141">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a360e-142">父元素</span><span class="sxs-lookup"><span data-stu-id="a360e-142">Parent Elements</span></span>  
  
|<span data-ttu-id="a360e-143">元素</span><span class="sxs-lookup"><span data-stu-id="a360e-143">Element</span></span>|<span data-ttu-id="a360e-144">描述</span><span class="sxs-lookup"><span data-stu-id="a360e-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a360e-145">serviceModel</span><span class="sxs-lookup"><span data-stu-id="a360e-145">serviceModel</span></span>|<span data-ttu-id="a360e-146">所有 Windows Communication Foundation (WCF) 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="a360e-146">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a360e-147">备注</span><span class="sxs-lookup"><span data-stu-id="a360e-147">Remarks</span></span>  
 <span data-ttu-id="a360e-148">默认情况下，WCF 服务和 ASP.NET 一起在寄宿应用程序域 (AppDomain) 中并行运行。</span><span class="sxs-lookup"><span data-stu-id="a360e-148">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="a360e-149">即使 WCF 和 ASP.NET 可以在同一 AppDomain 中共存，但在默认情况下，ASP.NET HTTP 管道不会处理 WCF 请求。</span><span class="sxs-lookup"><span data-stu-id="a360e-149">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="a360e-150">因此，WCF 服务不能使用 ASP.NET 应用程序平台的一些元素，</span><span class="sxs-lookup"><span data-stu-id="a360e-150">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="a360e-151">其中包括</span><span class="sxs-lookup"><span data-stu-id="a360e-151">These include</span></span>  
  
- <span data-ttu-id="a360e-152">ASP.NET File/URL 授权</span><span class="sxs-lookup"><span data-stu-id="a360e-152">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="a360e-153">ASP.NET 模拟</span><span class="sxs-lookup"><span data-stu-id="a360e-153">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="a360e-154">基于 Cookie 的会话状态</span><span class="sxs-lookup"><span data-stu-id="a360e-154">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="a360e-155">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="a360e-155">HttpContext.Current</span></span>  
  
- <span data-ttu-id="a360e-156">通过自定义 HttpModule 获得的管道扩展性</span><span class="sxs-lookup"><span data-stu-id="a360e-156">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="a360e-157">如果要使 WCF 服务在 ASP.NET 上下文中正常工作并仅通过 HTTP 进行通信，则可以使用 WCF 的 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="a360e-157">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="a360e-158">当 `aspNetCompatibilityEnabled` 属性在应用程序级别中设置为 `true` 时，此模式将启用。</span><span class="sxs-lookup"><span data-stu-id="a360e-158">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="a360e-159">服务实现必须使用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 类来声明其可以在兼容模式中运行。</span><span class="sxs-lookup"><span data-stu-id="a360e-159">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="a360e-160">当启用此兼容模式时，</span><span class="sxs-lookup"><span data-stu-id="a360e-160">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="a360e-161">ASP.NET File/URL 授权将在 WCF 授权之前强制执行。</span><span class="sxs-lookup"><span data-stu-id="a360e-161">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="a360e-162">授权决定是基于请求的传输级标识的。</span><span class="sxs-lookup"><span data-stu-id="a360e-162">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="a360e-163">消息级别的标识将被忽略。</span><span class="sxs-lookup"><span data-stu-id="a360e-163">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="a360e-164">WCF 服务操作开始是在 ASP.NET 模拟上下文中执行的。</span><span class="sxs-lookup"><span data-stu-id="a360e-164">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="a360e-165">如果为某个特定服务同时启用了 ASP.NET 模拟和 WCF 模拟，则将应用 WCF 模拟上下文。</span><span class="sxs-lookup"><span data-stu-id="a360e-165">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="a360e-166">可以通过 WCF 服务代码使用 HttpContext.Current，并且阻止服务公开非 HTTP 终结点。</span><span class="sxs-lookup"><span data-stu-id="a360e-166">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="a360e-167">WCF 请求由 ASP.NET 管道处理。</span><span class="sxs-lookup"><span data-stu-id="a360e-167">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="a360e-168">已配置为对传入请求执行操作的 HttpModule 也可以处理 WCF 请求。</span><span class="sxs-lookup"><span data-stu-id="a360e-168">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="a360e-169">这些 HttpModule 可包括 ASP.NET 平台组件（如 <xref:System.Web.SessionState.SessionStateModule>）以及自定义第三方模块。</span><span class="sxs-lookup"><span data-stu-id="a360e-169">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a360e-170">示例</span><span class="sxs-lookup"><span data-stu-id="a360e-170">Example</span></span>  
 <span data-ttu-id="a360e-171">下面的代码示例演示如何启用 ASP 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="a360e-171">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="a360e-172">代码</span><span class="sxs-lookup"><span data-stu-id="a360e-172">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="a360e-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="a360e-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="a360e-174">承载</span><span class="sxs-lookup"><span data-stu-id="a360e-174">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="a360e-175">WCF 服务和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a360e-175">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
