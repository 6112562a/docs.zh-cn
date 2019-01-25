---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 502fc5dd14d7bc3d979153607e1eeeb9354031bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737424"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="ea2e9-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="ea2e9-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="ea2e9-103">设置指定的声明类型<xref:System.Security.Principal.IIdentity.Name%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ea2e9-104">声明类型用于搜索<xref:System.Security.Claims.Claim>中的集合<xref:System.Security.Claims.ClaimsIdentity>返回的对象<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>此令牌处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="ea2e9-105">然后，将匹配声明的值设置为的名称<xref:System.Security.Principal.IIdentity>生成的此令牌处理程序。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="ea2e9-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ea2e9-106">\<system.identityModel></span></span>  
<span data-ttu-id="ea2e9-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ea2e9-107">\<identityConfiguration></span></span>  
<span data-ttu-id="ea2e9-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ea2e9-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ea2e9-109">\<add></span><span class="sxs-lookup"><span data-stu-id="ea2e9-109">\<add></span></span>  
<span data-ttu-id="ea2e9-110">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ea2e9-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="ea2e9-111">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="ea2e9-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2e9-112">语法</span><span class="sxs-lookup"><span data-stu-id="ea2e9-112">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea2e9-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ea2e9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ea2e9-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea2e9-115">特性</span><span class="sxs-lookup"><span data-stu-id="ea2e9-115">Attributes</span></span>  
  
|<span data-ttu-id="ea2e9-116">特性</span><span class="sxs-lookup"><span data-stu-id="ea2e9-116">Attribute</span></span>|<span data-ttu-id="ea2e9-117">描述</span><span class="sxs-lookup"><span data-stu-id="ea2e9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea2e9-118">值</span><span class="sxs-lookup"><span data-stu-id="ea2e9-118">value</span></span>|<span data-ttu-id="ea2e9-119">一个字符串，指定表示要使用的声明的声明类型的 URI<xref:System.Security.Principal.IIdentity.Name%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ea2e9-120">必需。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea2e9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="ea2e9-121">Child Elements</span></span>  
 <span data-ttu-id="ea2e9-122">无</span><span class="sxs-lookup"><span data-stu-id="ea2e9-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea2e9-123">父元素</span><span class="sxs-lookup"><span data-stu-id="ea2e9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea2e9-124">元素</span><span class="sxs-lookup"><span data-stu-id="ea2e9-124">Element</span></span>|<span data-ttu-id="ea2e9-125">描述</span><span class="sxs-lookup"><span data-stu-id="ea2e9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea2e9-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ea2e9-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="ea2e9-127">提供用于配置<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>类，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>类或这些类的任何一个的派生的类。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea2e9-128">备注</span><span class="sxs-lookup"><span data-stu-id="ea2e9-128">Remarks</span></span>  
 <span data-ttu-id="ea2e9-129">`<nameClaimType>`元素集<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>属性时<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>从配置初始化对象。</span><span class="sxs-lookup"><span data-stu-id="ea2e9-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2e9-130">示例</span><span class="sxs-lookup"><span data-stu-id="ea2e9-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea2e9-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="ea2e9-131">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
