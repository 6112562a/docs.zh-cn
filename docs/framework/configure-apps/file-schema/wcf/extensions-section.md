---
title: '&lt;extensions&gt; 节'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 92dd3c528290344d9537c51fccf7c13c74c1984a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145310"
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="46d5e-102">&lt;extensions&gt; 节</span><span class="sxs-lookup"><span data-stu-id="46d5e-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="46d5e-103">此配置节包含一个扩展集合，这些扩展使用户能够创建扩展的用户定义绑定、行为和其他方面。</span><span class="sxs-lookup"><span data-stu-id="46d5e-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="46d5e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="46d5e-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d5e-105">语法</span><span class="sxs-lookup"><span data-stu-id="46d5e-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46d5e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="46d5e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="46d5e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46d5e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46d5e-108">特性</span><span class="sxs-lookup"><span data-stu-id="46d5e-108">Attributes</span></span>  
 <span data-ttu-id="46d5e-109">无。</span><span class="sxs-lookup"><span data-stu-id="46d5e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46d5e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="46d5e-110">Child Elements</span></span>  
  
|<span data-ttu-id="46d5e-111">元素</span><span class="sxs-lookup"><span data-stu-id="46d5e-111">Element</span></span>|<span data-ttu-id="46d5e-112">描述</span><span class="sxs-lookup"><span data-stu-id="46d5e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46d5e-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="46d5e-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="46d5e-114">本节包含子元素，这些子元素指定使用户可以自定义服务或终结点行为的行为扩展。</span><span class="sxs-lookup"><span data-stu-id="46d5e-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="46d5e-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="46d5e-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="46d5e-116">本节为使用计算机或应用程序配置文件中的自定义绑定元素提供支持。</span><span class="sxs-lookup"><span data-stu-id="46d5e-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="46d5e-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="46d5e-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="46d5e-118">本节包含子元素，这些子元素指定使用户可以自定义绑定的绑定扩展。</span><span class="sxs-lookup"><span data-stu-id="46d5e-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="46d5e-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="46d5e-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="46d5e-120">本节包含元注册标准终结点的子元素。</span><span class="sxs-lookup"><span data-stu-id="46d5e-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46d5e-121">父元素</span><span class="sxs-lookup"><span data-stu-id="46d5e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="46d5e-122">元素</span><span class="sxs-lookup"><span data-stu-id="46d5e-122">Element</span></span>|<span data-ttu-id="46d5e-123">描述</span><span class="sxs-lookup"><span data-stu-id="46d5e-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46d5e-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="46d5e-124">system.ServiceModel</span></span>|<span data-ttu-id="46d5e-125">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="46d5e-125">The root element of all WCF configuration elements.</span></span>|
