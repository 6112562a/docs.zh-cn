---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: bb443334e0713464e64ec9297bbab4ad11eda723
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145050"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="23f6a-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="23f6a-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="23f6a-103">包含应用程序以客户端形式参与服务发现过程所需的设置。</span><span class="sxs-lookup"><span data-stu-id="23f6a-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="23f6a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23f6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="23f6a-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="23f6a-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f6a-106">语法</span><span class="sxs-lookup"><span data-stu-id="23f6a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23f6a-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="23f6a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="23f6a-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="23f6a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23f6a-109">特性</span><span class="sxs-lookup"><span data-stu-id="23f6a-109">Attributes</span></span>  
  
|<span data-ttu-id="23f6a-110">特性</span><span class="sxs-lookup"><span data-stu-id="23f6a-110">Attribute</span></span>|<span data-ttu-id="23f6a-111">描述</span><span class="sxs-lookup"><span data-stu-id="23f6a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23f6a-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="23f6a-112">discoveryEndpoint</span></span>|<span data-ttu-id="23f6a-113">一个包含发现终结点名称的字符串。通过此终结点，客户端应用程序能够自动搜索可检测服务，并能够在运行时查找服务地址。</span><span class="sxs-lookup"><span data-stu-id="23f6a-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23f6a-114">子元素</span><span class="sxs-lookup"><span data-stu-id="23f6a-114">Child Elements</span></span>  
  
|<span data-ttu-id="23f6a-115">元素</span><span class="sxs-lookup"><span data-stu-id="23f6a-115">Element</span></span>|<span data-ttu-id="23f6a-116">描述</span><span class="sxs-lookup"><span data-stu-id="23f6a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23f6a-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="23f6a-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="23f6a-118">一个配置元素，提供客户端应用程序用于搜索发现服务的一组条件。</span><span class="sxs-lookup"><span data-stu-id="23f6a-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="23f6a-119">条件可以划分为搜索条件 （指定要查找的服务） 和查找终止条件 （搜索应持续多久）。</span><span class="sxs-lookup"><span data-stu-id="23f6a-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23f6a-120">父元素</span><span class="sxs-lookup"><span data-stu-id="23f6a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="23f6a-121">元素</span><span class="sxs-lookup"><span data-stu-id="23f6a-121">Element</span></span>|<span data-ttu-id="23f6a-122">描述</span><span class="sxs-lookup"><span data-stu-id="23f6a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23f6a-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="23f6a-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="23f6a-124">定义一个标准终结点，应用程序通过利用该终结点包含的信息，能够充当可在运行时动态查找终结点地址的客户端程序。</span><span class="sxs-lookup"><span data-stu-id="23f6a-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23f6a-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="23f6a-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
