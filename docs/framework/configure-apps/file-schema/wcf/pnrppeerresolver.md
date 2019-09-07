---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400055"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="8833c-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="8833c-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="8833c-102">指定要将 PNRP（对等名称解析协议）解析程序用作解析程序。</span><span class="sxs-lookup"><span data-stu-id="8833c-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="8833c-103">此元素是可选的，因为 PNRP 是默认解析程序。</span><span class="sxs-lookup"><span data-stu-id="8833c-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="8833c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8833c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8833c-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8833c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8833c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<绑定 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8833c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8833c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="8833c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="8833c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<绑定 >** </span><span class="sxs-lookup"><span data-stu-id="8833c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8833c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="8833c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8833c-110">语法</span><span class="sxs-lookup"><span data-stu-id="8833c-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8833c-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8833c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8833c-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8833c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8833c-113">特性</span><span class="sxs-lookup"><span data-stu-id="8833c-113">Attributes</span></span>  
  
|<span data-ttu-id="8833c-114">特性</span><span class="sxs-lookup"><span data-stu-id="8833c-114">Attribute</span></span>|<span data-ttu-id="8833c-115">描述</span><span class="sxs-lookup"><span data-stu-id="8833c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8833c-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="8833c-116">resolverType</span></span>|<span data-ttu-id="8833c-117">一个字符串，指定要使用的解析程序。</span><span class="sxs-lookup"><span data-stu-id="8833c-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="8833c-118">此属性是可选的。</span><span class="sxs-lookup"><span data-stu-id="8833c-118">This attribute is optional.</span></span> <span data-ttu-id="8833c-119">如果不设置，或者将其设置为空字符串，则使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="8833c-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8833c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="8833c-120">Child Elements</span></span>  
 <span data-ttu-id="8833c-121">无</span><span class="sxs-lookup"><span data-stu-id="8833c-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8833c-122">父元素</span><span class="sxs-lookup"><span data-stu-id="8833c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8833c-123">元素</span><span class="sxs-lookup"><span data-stu-id="8833c-123">Element</span></span>|<span data-ttu-id="8833c-124">描述</span><span class="sxs-lookup"><span data-stu-id="8833c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8833c-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="8833c-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="8833c-126">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="8833c-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8833c-127">示例</span><span class="sxs-lookup"><span data-stu-id="8833c-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="8833c-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="8833c-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8833c-129">绑定</span><span class="sxs-lookup"><span data-stu-id="8833c-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8833c-130">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="8833c-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8833c-131">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="8833c-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8833c-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8833c-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="8833c-133">对等解析程序</span><span class="sxs-lookup"><span data-stu-id="8833c-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
