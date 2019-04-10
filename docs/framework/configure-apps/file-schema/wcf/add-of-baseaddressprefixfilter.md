---
title: <add> 的 <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: a58a29e44fff3d653d04da271e3b240f2969611f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143892"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="e6e0c-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="e6e0c-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="e6e0c-103">表示一个配置元素，指定传递筛选器，它提供一种机制，托管在 IIS 中的 Windows Communication Foundation (WCF) 应用程序时可选取适当的 Internet 信息服务 (IIS) 绑定。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="e6e0c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6e0c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6e0c-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e6e0c-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="e6e0c-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="e6e0c-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="e6e0c-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e6e0c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e0c-108">语法</span><span class="sxs-lookup"><span data-stu-id="e6e0c-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6e0c-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e6e0c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e6e0c-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6e0c-111">特性</span><span class="sxs-lookup"><span data-stu-id="e6e0c-111">Attributes</span></span>  
  
|<span data-ttu-id="e6e0c-112">特性</span><span class="sxs-lookup"><span data-stu-id="e6e0c-112">Attribute</span></span>|<span data-ttu-id="e6e0c-113">描述</span><span class="sxs-lookup"><span data-stu-id="e6e0c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6e0c-114">prefix</span><span class="sxs-lookup"><span data-stu-id="e6e0c-114">prefix</span></span>|<span data-ttu-id="e6e0c-115">用于与基址的一部分进行匹配的 URI。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6e0c-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e6e0c-116">Child Elements</span></span>  
 <span data-ttu-id="e6e0c-117">无。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6e0c-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e6e0c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e6e0c-119">元素</span><span class="sxs-lookup"><span data-stu-id="e6e0c-119">Element</span></span>|<span data-ttu-id="e6e0c-120">描述</span><span class="sxs-lookup"><span data-stu-id="e6e0c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6e0c-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="e6e0c-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="e6e0c-122">指定传递筛选器提供了一种机制来承载在 IIS 中的 Windows Communication Foundation (WCF) 应用程序时选择适当的 IIS 绑定的配置元素的集合。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6e0c-123">备注</span><span class="sxs-lookup"><span data-stu-id="e6e0c-123">Remarks</span></span>  
 <span data-ttu-id="e6e0c-124">前缀筛选器为共享的宿主提供程序提供一种指定服务要使用的 URI 的方法。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="e6e0c-125">它使得共享主机可以在同一站点上通过同一方案的不同基址承载多个应用程序。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="e6e0c-126">IIS 网站是包含虚拟目录的虚拟应用程序的容器。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="e6e0c-127">可通过一个或多个 IIS 绑定访问站点上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="e6e0c-128">IIS 绑定提供两条信息：绑定协议和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="e6e0c-129">绑定协议（例如 HTTP）定义发生通信所基于的方案，而绑定信息（例如 IP 地址、端口、主机头）包含用于访问站点的数据。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="e6e0c-130">IIS 支持为每个站点指定多个 IIS 绑定，这会导致每个方案有多个基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="e6e0c-131">由于一个站点下承载的 WCF 服务允许每个方案只能有一个基址的绑定，可以使用前缀筛选器功能选取所需的托管服务的基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="e6e0c-132">根据可选前缀列表筛选器筛选 IIS 提供的传入基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="e6e0c-133">例如，您的站点可包含以下基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="e6e0c-134">可以使用下面的配置文件在 appdomain 级指定前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="e6e0c-135">在此示例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 是允许传递的各自方案的唯一基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="e6e0c-136">默认情况下，未指定前缀时，将传递所有地址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="e6e0c-137">而指定前缀后，将只允许传递该方案的匹配基址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6e0c-138">筛选器不支持任何通配符。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="e6e0c-139">此外，IIS 提供的基址可能有绑定到在 `baseAddressPrefixFilters` 列表中未列出的其他方案的地址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="e6e0c-140">不会筛选出这些地址。</span><span class="sxs-lookup"><span data-stu-id="e6e0c-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e0c-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6e0c-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="e6e0c-142">宿主</span><span class="sxs-lookup"><span data-stu-id="e6e0c-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
