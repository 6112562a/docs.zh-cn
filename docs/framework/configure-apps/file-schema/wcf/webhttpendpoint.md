---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940473"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="e5ee7-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="e5ee7-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="e5ee7-102">此配置元素定义一个标准终结点, 该终结点具有固定[ \<的 webHttpBinding >](webhttpbinding.md)绑定[ \<](webhttp.md) , 可自动添加 wcf-webhttp > 行为。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="e5ee7-103">在编写 REST 服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="e5ee7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5ee7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5ee7-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e5ee7-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ee7-106">语法</span><span class="sxs-lookup"><span data-stu-id="e5ee7-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5ee7-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e5ee7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e5ee7-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5ee7-109">特性</span><span class="sxs-lookup"><span data-stu-id="e5ee7-109">Attributes</span></span>  
  
|<span data-ttu-id="e5ee7-110">特性</span><span class="sxs-lookup"><span data-stu-id="e5ee7-110">Attribute</span></span>|<span data-ttu-id="e5ee7-111">描述</span><span class="sxs-lookup"><span data-stu-id="e5ee7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5ee7-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="e5ee7-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="e5ee7-113">一个布尔值，指示是否启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="e5ee7-114">如果启用了自动格式选择，基础结构将分析请求消息的 `Accept` 标头，并确定最适合的响应格式。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="e5ee7-115">如果 `Accept` 标头未指定适合的响应格式，则基础结构将使用请求消息的 `Content-Type`，或使用操作的默认响应格式。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="e5ee7-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="e5ee7-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="e5ee7-117">一个指定默认传出响应格式的特性。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="e5ee7-118">此特性的类型为 <xref:System.ServiceModel.Web.WebMessageFormat></span><span class="sxs-lookup"><span data-stu-id="e5ee7-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="e5ee7-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="e5ee7-119">helpEnabled</span></span>|<span data-ttu-id="e5ee7-120">一个布尔值，指示是否为终结点启用了 HTTP 帮助页。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="e5ee7-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e5ee7-121">webEndpointType</span></span>|<span data-ttu-id="e5ee7-122">一个字符串，指定终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5ee7-123">子元素</span><span class="sxs-lookup"><span data-stu-id="e5ee7-123">Child Elements</span></span>  
 <span data-ttu-id="e5ee7-124">无。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5ee7-125">父元素</span><span class="sxs-lookup"><span data-stu-id="e5ee7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5ee7-126">元素</span><span class="sxs-lookup"><span data-stu-id="e5ee7-126">Element</span></span>|<span data-ttu-id="e5ee7-127">描述</span><span class="sxs-lookup"><span data-stu-id="e5ee7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5ee7-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e5ee7-128">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e5ee7-129">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="e5ee7-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5ee7-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5ee7-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
