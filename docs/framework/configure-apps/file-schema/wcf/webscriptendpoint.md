---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: acafb5b6a5c4911dcf21a55cfb9e93883067e5ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566380"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="77cf7-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="77cf7-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="77cf7-103">此配置元素定义具有固定的标准终结点[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)自动绑定，它将添加[ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)行为。</span><span class="sxs-lookup"><span data-stu-id="77cf7-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="77cf7-104">在编写从 ASP.NET AJAX 应用程序中调用的服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="77cf7-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="77cf7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="77cf7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="77cf7-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="77cf7-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cf7-107">语法</span><span class="sxs-lookup"><span data-stu-id="77cf7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77cf7-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="77cf7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="77cf7-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="77cf7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77cf7-110">特性</span><span class="sxs-lookup"><span data-stu-id="77cf7-110">Attributes</span></span>  
  
|<span data-ttu-id="77cf7-111">特性</span><span class="sxs-lookup"><span data-stu-id="77cf7-111">Attribute</span></span>|<span data-ttu-id="77cf7-112">描述</span><span class="sxs-lookup"><span data-stu-id="77cf7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77cf7-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="77cf7-113">webEndpointType</span></span>|<span data-ttu-id="77cf7-114">一个字符串，指定终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="77cf7-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77cf7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="77cf7-115">Child Elements</span></span>  
 <span data-ttu-id="77cf7-116">无。</span><span class="sxs-lookup"><span data-stu-id="77cf7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77cf7-117">父元素</span><span class="sxs-lookup"><span data-stu-id="77cf7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="77cf7-118">元素</span><span class="sxs-lookup"><span data-stu-id="77cf7-118">Element</span></span>|<span data-ttu-id="77cf7-119">描述</span><span class="sxs-lookup"><span data-stu-id="77cf7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77cf7-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="77cf7-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="77cf7-121">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="77cf7-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77cf7-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="77cf7-122">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
