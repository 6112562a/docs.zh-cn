---
title: '&lt;issuedTokenParameters&gt; 的 &lt;issuer&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 58fdd93eb4f69e48783873df26bf1c35a2a849e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539150"
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="4dc94-102">&lt;issuedTokenParameters&gt; 的 &lt;issuer&gt;</span><span class="sxs-lookup"><span data-stu-id="4dc94-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="4dc94-103">指定颁发安全令牌的安全令牌服务 (STS)。</span><span class="sxs-lookup"><span data-stu-id="4dc94-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="4dc94-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4dc94-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4dc94-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4dc94-105">\<bindings></span></span>  
<span data-ttu-id="4dc94-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4dc94-106">\<customBinding></span></span>  
<span data-ttu-id="4dc94-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="4dc94-107">\<binding></span></span>  
<span data-ttu-id="4dc94-108">\<安全 ></span><span class="sxs-lookup"><span data-stu-id="4dc94-108">\<security></span></span>  
<span data-ttu-id="4dc94-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="4dc94-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="4dc94-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="4dc94-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc94-111">语法</span><span class="sxs-lookup"><span data-stu-id="4dc94-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dc94-112">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4dc94-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4dc94-113">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4dc94-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dc94-114">特性</span><span class="sxs-lookup"><span data-stu-id="4dc94-114">Attributes</span></span>  
  
|<span data-ttu-id="4dc94-115">特性</span><span class="sxs-lookup"><span data-stu-id="4dc94-115">Attribute</span></span>|<span data-ttu-id="4dc94-116">描述</span><span class="sxs-lookup"><span data-stu-id="4dc94-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dc94-117">address</span><span class="sxs-lookup"><span data-stu-id="4dc94-117">address</span></span>|<span data-ttu-id="4dc94-118">必选字符串。</span><span class="sxs-lookup"><span data-stu-id="4dc94-118">Required string.</span></span> <span data-ttu-id="4dc94-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="4dc94-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dc94-120">子元素</span><span class="sxs-lookup"><span data-stu-id="4dc94-120">Child Elements</span></span>  
  
|<span data-ttu-id="4dc94-121">元素</span><span class="sxs-lookup"><span data-stu-id="4dc94-121">Element</span></span>|<span data-ttu-id="4dc94-122">描述</span><span class="sxs-lookup"><span data-stu-id="4dc94-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc94-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="4dc94-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="4dc94-124">生成器可以创建的终结点的地址标头的集合。</span><span class="sxs-lookup"><span data-stu-id="4dc94-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="4dc94-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="4dc94-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4dc94-126">在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="4dc94-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dc94-127">父元素</span><span class="sxs-lookup"><span data-stu-id="4dc94-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4dc94-128">元素</span><span class="sxs-lookup"><span data-stu-id="4dc94-128">Element</span></span>|<span data-ttu-id="4dc94-129">描述</span><span class="sxs-lookup"><span data-stu-id="4dc94-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc94-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="4dc94-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="4dc94-131">指定当前颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="4dc94-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dc94-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="4dc94-132">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4dc94-133">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="4dc94-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4dc94-134">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="4dc94-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4dc94-135">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="4dc94-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4dc94-136">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="4dc94-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4dc94-137">绑定</span><span class="sxs-lookup"><span data-stu-id="4dc94-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4dc94-138">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="4dc94-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4dc94-139">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="4dc94-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4dc94-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4dc94-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="4dc94-141">如何：创建自定义绑定使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4dc94-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="4dc94-142">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="4dc94-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
