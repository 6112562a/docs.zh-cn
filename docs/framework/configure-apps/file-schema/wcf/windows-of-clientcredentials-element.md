---
title: <windows>of <clientCredentials>元素
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940298"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="815fb-102">\<clientCredentials > 元素\<的 windows ></span><span class="sxs-lookup"><span data-stu-id="815fb-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="815fb-103">指定用于表示客户端的 Windows 凭据的设置。</span><span class="sxs-lookup"><span data-stu-id="815fb-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="815fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="815fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="815fb-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="815fb-105">\<behaviors></span></span>  
<span data-ttu-id="815fb-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="815fb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="815fb-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="815fb-107">\<behavior></span></span>  
<span data-ttu-id="815fb-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="815fb-108">\<clientCredentials></span></span>  
<span data-ttu-id="815fb-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="815fb-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815fb-110">语法</span><span class="sxs-lookup"><span data-stu-id="815fb-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="815fb-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="815fb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="815fb-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="815fb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="815fb-113">特性</span><span class="sxs-lookup"><span data-stu-id="815fb-113">Attributes</span></span>  
  
|<span data-ttu-id="815fb-114">特性</span><span class="sxs-lookup"><span data-stu-id="815fb-114">Attribute</span></span>|<span data-ttu-id="815fb-115">描述</span><span class="sxs-lookup"><span data-stu-id="815fb-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="815fb-116">设置客户端用于与服务器进行通信的模拟首选项。</span><span class="sxs-lookup"><span data-stu-id="815fb-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="815fb-117">服务器上不强制使用客户端所选择的模拟模式。</span><span class="sxs-lookup"><span data-stu-id="815fb-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="815fb-118">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="815fb-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="815fb-119">标识服务器可以获取客户端的标识和特权, 但不能模拟客户端。</span><span class="sxs-lookup"><span data-stu-id="815fb-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="815fb-120">模仿服务器可以在本地系统上模拟客户端的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="815fb-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="815fb-121">委托服务器可以模拟客户端在远程系统上的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="815fb-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="815fb-122">匿名服务器无法模拟或标识客户端。</span><span class="sxs-lookup"><span data-stu-id="815fb-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="815fb-123">内容未分配模拟级别。</span><span class="sxs-lookup"><span data-stu-id="815fb-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="815fb-124">默认值为 Identification。</span><span class="sxs-lookup"><span data-stu-id="815fb-124">The default is Identification.</span></span> <span data-ttu-id="815fb-125">此属性的类型为 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="815fb-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="815fb-126">如果 Kerberos 不可用，则将此属性设置为 `true` 可令身份验证降级到 NTLM。</span><span class="sxs-lookup"><span data-stu-id="815fb-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="815fb-127">如果将此属性`false`设置为, 则会导致 Windows Communication Foundation (WCF) 在使用 NTLM 时尽力引发异常。</span><span class="sxs-lookup"><span data-stu-id="815fb-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="815fb-128">请注意，将此属性设置为 `false` 可能不阻止通过网络发送 NTLM 凭据。</span><span class="sxs-lookup"><span data-stu-id="815fb-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="815fb-129">子元素</span><span class="sxs-lookup"><span data-stu-id="815fb-129">Child Elements</span></span>  
 <span data-ttu-id="815fb-130">无。</span><span class="sxs-lookup"><span data-stu-id="815fb-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="815fb-131">父元素</span><span class="sxs-lookup"><span data-stu-id="815fb-131">Parent Elements</span></span>  
  
|<span data-ttu-id="815fb-132">元素</span><span class="sxs-lookup"><span data-stu-id="815fb-132">Element</span></span>|<span data-ttu-id="815fb-133">描述</span><span class="sxs-lookup"><span data-stu-id="815fb-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="815fb-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="815fb-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="815fb-135">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="815fb-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="815fb-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="815fb-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="815fb-137">保护客户端</span><span class="sxs-lookup"><span data-stu-id="815fb-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="815fb-138">使用证书</span><span class="sxs-lookup"><span data-stu-id="815fb-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="815fb-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="815fb-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
