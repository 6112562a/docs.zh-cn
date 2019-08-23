---
title: <add> 的 <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926884"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="1db23-102">\<添加 allowedAudienceUris > \<的 ></span><span class="sxs-lookup"><span data-stu-id="1db23-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="1db23-103">添加 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI，只有在使用该目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="1db23-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="1db23-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1db23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1db23-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="1db23-105">\<behaviors></span></span>  
<span data-ttu-id="1db23-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1db23-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1db23-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="1db23-107">\<behavior></span></span>  
<span data-ttu-id="1db23-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1db23-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1db23-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="1db23-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="1db23-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="1db23-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="1db23-111">\<添加 allowedAudienceUris 的\<> 元素 ></span><span class="sxs-lookup"><span data-stu-id="1db23-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db23-112">语法</span><span class="sxs-lookup"><span data-stu-id="1db23-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db23-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1db23-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1db23-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1db23-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db23-115">特性</span><span class="sxs-lookup"><span data-stu-id="1db23-115">Attributes</span></span>  
  
|<span data-ttu-id="1db23-116">特性</span><span class="sxs-lookup"><span data-stu-id="1db23-116">Attribute</span></span>|<span data-ttu-id="1db23-117">描述</span><span class="sxs-lookup"><span data-stu-id="1db23-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1db23-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="1db23-118">allowedAudienceUri</span></span>|<span data-ttu-id="1db23-119">一个包含 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 的字符串，只有在使用该目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="1db23-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1db23-120">子元素</span><span class="sxs-lookup"><span data-stu-id="1db23-120">Child Elements</span></span>  
 <span data-ttu-id="1db23-121">无。</span><span class="sxs-lookup"><span data-stu-id="1db23-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1db23-122">父元素</span><span class="sxs-lookup"><span data-stu-id="1db23-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1db23-123">元素</span><span class="sxs-lookup"><span data-stu-id="1db23-123">Element</span></span>|<span data-ttu-id="1db23-124">描述</span><span class="sxs-lookup"><span data-stu-id="1db23-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1db23-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="1db23-125">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="1db23-126">表示 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 集合，只有在使用这些目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="1db23-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db23-127">备注</span><span class="sxs-lookup"><span data-stu-id="1db23-127">Remarks</span></span>  
 <span data-ttu-id="1db23-128">在采用颁发 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的安全令牌服务 (STS) 的联合应用程序中，应使用此集合。</span><span class="sxs-lookup"><span data-stu-id="1db23-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="1db23-129">当 STS 颁发安全令牌时，它可以通过将 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 添加到安全令牌中，来指定安全令牌的目标 Web 服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="1db23-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="1db23-130">这样，通过指定应采用以下方式执行此检查，接收方 Web 服务的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 将能够验证颁发的安全令牌是否针对此 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="1db23-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="1db23-131">将 `audienceUriMode` 的 `<issuedTokenAuthentication>` 属性设置为 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="1db23-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="1db23-132">将有效 URI 添加到此集合，以指定有效 URI 集。</span><span class="sxs-lookup"><span data-stu-id="1db23-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="1db23-133">有关详细信息，请参阅 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="1db23-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="1db23-134">有关使用此配置元素的详细信息, 请[参阅如何:在联合身份验证服务](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上配置凭据。</span><span class="sxs-lookup"><span data-stu-id="1db23-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db23-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="1db23-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="1db23-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="1db23-136">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="1db23-137">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="1db23-137">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="1db23-138">安全行为</span><span class="sxs-lookup"><span data-stu-id="1db23-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="1db23-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="1db23-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1db23-140">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="1db23-140">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
