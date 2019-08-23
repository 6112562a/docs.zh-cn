---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940615"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="75fa3-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="75fa3-101">\<useManagedPresentation></span></span>
<span data-ttu-id="75fa3-102">一个绑定元素，用于与支持 WS-Trust 的 CardSpace 配置文件的 CardSpace 安全令牌服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="75fa3-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="75fa3-103">此元素没有属性并且以空开关形式存在。</span><span class="sxs-lookup"><span data-stu-id="75fa3-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="75fa3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75fa3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="75fa3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="75fa3-105">\<bindings></span></span>  
<span data-ttu-id="75fa3-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="75fa3-106">\<customBinding></span></span>  
<span data-ttu-id="75fa3-107">\<绑定 ></span><span class="sxs-lookup"><span data-stu-id="75fa3-107">\<binding></span></span>  
<span data-ttu-id="75fa3-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="75fa3-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fa3-109">语法</span><span class="sxs-lookup"><span data-stu-id="75fa3-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75fa3-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="75fa3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75fa3-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="75fa3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75fa3-112">特性</span><span class="sxs-lookup"><span data-stu-id="75fa3-112">Attributes</span></span>  
 <span data-ttu-id="75fa3-113">无。</span><span class="sxs-lookup"><span data-stu-id="75fa3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75fa3-114">子元素</span><span class="sxs-lookup"><span data-stu-id="75fa3-114">Child Elements</span></span>  
 <span data-ttu-id="75fa3-115">无</span><span class="sxs-lookup"><span data-stu-id="75fa3-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75fa3-116">父元素</span><span class="sxs-lookup"><span data-stu-id="75fa3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="75fa3-117">元素</span><span class="sxs-lookup"><span data-stu-id="75fa3-117">Element</span></span>|<span data-ttu-id="75fa3-118">描述</span><span class="sxs-lookup"><span data-stu-id="75fa3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75fa3-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="75fa3-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="75fa3-120">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="75fa3-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75fa3-121">备注</span><span class="sxs-lookup"><span data-stu-id="75fa3-121">Remarks</span></span>  
 <span data-ttu-id="75fa3-122">标识提供程序使用此元素，用以在它的策略中表明它支持 WS-Trust 的 CardSpace 配置文件这一事实。</span><span class="sxs-lookup"><span data-stu-id="75fa3-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="75fa3-123">发布这种策略断言的标识提供程序应该能够基于该 CardSpace 配置文件颁发令牌。</span><span class="sxs-lookup"><span data-stu-id="75fa3-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fa3-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="75fa3-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="75fa3-125">绑定</span><span class="sxs-lookup"><span data-stu-id="75fa3-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="75fa3-126">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="75fa3-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="75fa3-127">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="75fa3-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="75fa3-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="75fa3-128">\<customBinding></span></span>](custombinding.md)
