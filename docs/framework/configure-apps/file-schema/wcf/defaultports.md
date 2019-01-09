---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7ddfddaa13778ce98bd93b6d8029438377fc7e94
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145180"
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="06fcd-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="06fcd-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="06fcd-103">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="06fcd-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="06fcd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06fcd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06fcd-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="06fcd-105">\<behaviors></span></span>  
<span data-ttu-id="06fcd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="06fcd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="06fcd-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="06fcd-107">\<behavior></span></span>  
<span data-ttu-id="06fcd-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="06fcd-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="06fcd-109">\<d d ></span><span class="sxs-lookup"><span data-stu-id="06fcd-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fcd-110">语法</span><span class="sxs-lookup"><span data-stu-id="06fcd-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06fcd-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="06fcd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06fcd-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="06fcd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06fcd-113">特性</span><span class="sxs-lookup"><span data-stu-id="06fcd-113">Attributes</span></span>  
 <span data-ttu-id="06fcd-114">无。</span><span class="sxs-lookup"><span data-stu-id="06fcd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06fcd-115">子元素</span><span class="sxs-lookup"><span data-stu-id="06fcd-115">Child Elements</span></span>  
  
|<span data-ttu-id="06fcd-116">元素</span><span class="sxs-lookup"><span data-stu-id="06fcd-116">Element</span></span>|<span data-ttu-id="06fcd-117">描述</span><span class="sxs-lookup"><span data-stu-id="06fcd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06fcd-118">\<添加 > 的\<d d ></span><span class="sxs-lookup"><span data-stu-id="06fcd-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="06fcd-119">客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="06fcd-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06fcd-120">父元素</span><span class="sxs-lookup"><span data-stu-id="06fcd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="06fcd-121">元素</span><span class="sxs-lookup"><span data-stu-id="06fcd-121">Element</span></span>|<span data-ttu-id="06fcd-122">描述</span><span class="sxs-lookup"><span data-stu-id="06fcd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06fcd-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="06fcd-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="06fcd-124">默认端口列表。</span><span class="sxs-lookup"><span data-stu-id="06fcd-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06fcd-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="06fcd-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
