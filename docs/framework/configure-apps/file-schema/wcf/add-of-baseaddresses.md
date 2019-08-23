---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920218"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="9d487-102">\<添加 baseAddresses > \<的 ></span><span class="sxs-lookup"><span data-stu-id="9d487-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="9d487-103">表示一个配置元素，该元素指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="9d487-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="9d487-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d487-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d487-105">\<客户端 ></span><span class="sxs-lookup"><span data-stu-id="9d487-105">\<client></span></span>  
<span data-ttu-id="9d487-106">\<终结点 ></span><span class="sxs-lookup"><span data-stu-id="9d487-106">\<endpoint></span></span>  
<span data-ttu-id="9d487-107">\<主机 ></span><span class="sxs-lookup"><span data-stu-id="9d487-107">\<host></span></span>  
<span data-ttu-id="9d487-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="9d487-108">\<baseAddresses></span></span>  
<span data-ttu-id="9d487-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="9d487-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d487-110">语法</span><span class="sxs-lookup"><span data-stu-id="9d487-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="9d487-111">类型</span><span class="sxs-lookup"><span data-stu-id="9d487-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d487-112">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9d487-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9d487-113">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9d487-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d487-114">特性</span><span class="sxs-lookup"><span data-stu-id="9d487-114">Attributes</span></span>  
  
|<span data-ttu-id="9d487-115">特性</span><span class="sxs-lookup"><span data-stu-id="9d487-115">Attribute</span></span>|<span data-ttu-id="9d487-116">描述</span><span class="sxs-lookup"><span data-stu-id="9d487-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="9d487-117">一个字符串，指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="9d487-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d487-118">子元素</span><span class="sxs-lookup"><span data-stu-id="9d487-118">Child Elements</span></span>  
 <span data-ttu-id="9d487-119">无。</span><span class="sxs-lookup"><span data-stu-id="9d487-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d487-120">父元素</span><span class="sxs-lookup"><span data-stu-id="9d487-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9d487-121">元素</span><span class="sxs-lookup"><span data-stu-id="9d487-121">Element</span></span>|<span data-ttu-id="9d487-122">描述</span><span class="sxs-lookup"><span data-stu-id="9d487-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d487-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="9d487-123">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="9d487-124">一个 `baseAddress` 元素集合。</span><span class="sxs-lookup"><span data-stu-id="9d487-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d487-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="9d487-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="9d487-126">承载</span><span class="sxs-lookup"><span data-stu-id="9d487-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
