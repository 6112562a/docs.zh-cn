---
title: '&lt;claimTypeRequirements&gt; 的 &lt;add&gt; 元素'
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: fb5e723f6cff9f6e573a45a1dabe008beb9399e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687307"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="8a2d9-102">&lt;claimTypeRequirements&gt; 的 &lt;add&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="8a2d9-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="8a2d9-103">指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="8a2d9-104">例如，服务规定有关传入凭据的要求，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="8a2d9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8a2d9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="8a2d9-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8a2d9-106">\<bindings></span></span>  
<span data-ttu-id="8a2d9-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="8a2d9-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="8a2d9-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="8a2d9-108">\<binding></span></span>  
<span data-ttu-id="8a2d9-109">\<安全 ></span><span class="sxs-lookup"><span data-stu-id="8a2d9-109">\<security></span></span>  
<span data-ttu-id="8a2d9-110">\<message></span><span class="sxs-lookup"><span data-stu-id="8a2d9-110">\<message></span></span>  
<span data-ttu-id="8a2d9-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8a2d9-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a2d9-112">语法</span><span class="sxs-lookup"><span data-stu-id="8a2d9-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a2d9-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8a2d9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8a2d9-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a2d9-115">特性</span><span class="sxs-lookup"><span data-stu-id="8a2d9-115">Attributes</span></span>  
  
|<span data-ttu-id="8a2d9-116">特性</span><span class="sxs-lookup"><span data-stu-id="8a2d9-116">Attribute</span></span>|<span data-ttu-id="8a2d9-117">描述</span><span class="sxs-lookup"><span data-stu-id="8a2d9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a2d9-118">claimType</span><span class="sxs-lookup"><span data-stu-id="8a2d9-118">claimType</span></span>|<span data-ttu-id="8a2d9-119">一个 URI，定义声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="8a2d9-120">例如，若要从网站上购买产品，用户必须提供具有足够信用额度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="8a2d9-121">声明类型将为信用卡 URI。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="8a2d9-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="8a2d9-122">isOptional</span></span>|<span data-ttu-id="8a2d9-123">一个布尔值，指定声明是否为可选的。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="8a2d9-124">如果声明是必选的，则将此属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="8a2d9-125">当服务请求一些并非必要的信息时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="8a2d9-126">例如，您可以要求用户输入其名、姓和地址，但决定其电话号码是可选的。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a2d9-127">子元素</span><span class="sxs-lookup"><span data-stu-id="8a2d9-127">Child Elements</span></span>  
 <span data-ttu-id="8a2d9-128">无。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a2d9-129">父元素</span><span class="sxs-lookup"><span data-stu-id="8a2d9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8a2d9-130">元素</span><span class="sxs-lookup"><span data-stu-id="8a2d9-130">Element</span></span>|<span data-ttu-id="8a2d9-131">描述</span><span class="sxs-lookup"><span data-stu-id="8a2d9-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a2d9-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8a2d9-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="8a2d9-133">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="8a2d9-134">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="8a2d9-135">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8a2d9-136">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8a2d9-137">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a2d9-138">备注</span><span class="sxs-lookup"><span data-stu-id="8a2d9-138">Remarks</span></span>  
 <span data-ttu-id="8a2d9-139">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8a2d9-140">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8a2d9-141">此要求出现在安全策略中。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="8a2d9-142">当客户端请求来自联合服务（例如 CardSpace）的凭据时，它会将需求放置在令牌请求 (RequestSecurityToken) 中，以便联合服务能够相应地颁发符合需求的凭据。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a2d9-143">示例</span><span class="sxs-lookup"><span data-stu-id="8a2d9-143">Example</span></span>  
 <span data-ttu-id="8a2d9-144">下面的配置将两个声明类型需求添加到安全绑定。</span><span class="sxs-lookup"><span data-stu-id="8a2d9-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="8a2d9-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a2d9-145">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
