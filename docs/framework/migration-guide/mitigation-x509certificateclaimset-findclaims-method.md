---
title: 缓解：X509CertificateClaimSet.FindClaims 方法
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc24cd494866c087860144f1720988ccfc2dfa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536433"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="60388-102">缓解：X509CertificateClaimSet.FindClaims 方法</span><span class="sxs-lookup"><span data-stu-id="60388-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="60388-103">从面向 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的应用开始，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法尝试将 `claimType` 参数与其 SAN 字段中的所有 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="60388-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="60388-104">影响</span><span class="sxs-lookup"><span data-stu-id="60388-104">Impact</span></span>  
 <span data-ttu-id="60388-105">此更改仅影响面向从 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 开始的 .NET Framework 版本的应用。</span><span class="sxs-lookup"><span data-stu-id="60388-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="60388-106">对于面向 .NET Framework 先前版本的应用，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法尝试仅将 `claimType` 参数与最后一个 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="60388-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="60388-107">缓解</span><span class="sxs-lookup"><span data-stu-id="60388-107">Mitigation</span></span>  
 <span data-ttu-id="60388-108">如果无需进行此更改，则面向从 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 开始的 .NET Framework 版本的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择放弃更改：</span><span class="sxs-lookup"><span data-stu-id="60388-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="60388-109">此外，面向 .NET Framework 以前版本但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 或更高版本下运行的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择实现此行为：</span><span class="sxs-lookup"><span data-stu-id="60388-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60388-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="60388-110">See also</span></span>
- [<span data-ttu-id="60388-111">重定目标更改</span><span class="sxs-lookup"><span data-stu-id="60388-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
