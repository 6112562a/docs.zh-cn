---
ms.openlocfilehash: 1ece2bb2d5e4ce93f201536d03aabeff5eb0012e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804310"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="c11f4-101">X509CertificateClaimSet.FindClaims 考虑到所有 claimTypes</span><span class="sxs-lookup"><span data-stu-id="c11f4-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c11f4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c11f4-102">Details</span></span>|<span data-ttu-id="c11f4-103">在面向 .NET Framework 4.6.1 的应用中，如果从 SAN 字段拥有多个 DNS 条目的证书初始化 X509 声明集，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法会尝试将 claimType 自变量与所有 DNS 条目进行匹配。对于面向以前版本的 .NET Framework 的应用，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法会尝试仅将 claimType 自变量与最后一个 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="c11f4-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> method attempts to match the claimType argument only with the last DNS entry.</span></span>|
|<span data-ttu-id="c11f4-104">建议</span><span class="sxs-lookup"><span data-stu-id="c11f4-104">Suggestion</span></span>|<span data-ttu-id="c11f4-105">此更改仅影响面向 .NET Framework 4.6.1 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c11f4-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="c11f4-106">在 [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 兼容性开关中，可能会禁用此更改（如果面向 4.6.1 之前的版本，将启用此更改）。</span><span class="sxs-lookup"><span data-stu-id="c11f4-106">This change may be disabled (or enabled if targetting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>|
|<span data-ttu-id="c11f4-107">范围</span><span class="sxs-lookup"><span data-stu-id="c11f4-107">Scope</span></span>|<span data-ttu-id="c11f4-108">次要</span><span class="sxs-lookup"><span data-stu-id="c11f4-108">Minor</span></span>|
|<span data-ttu-id="c11f4-109">版本</span><span class="sxs-lookup"><span data-stu-id="c11f4-109">Version</span></span>|<span data-ttu-id="c11f4-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c11f4-110">4.6.1</span></span>|
|<span data-ttu-id="c11f4-111">类型</span><span class="sxs-lookup"><span data-stu-id="c11f4-111">Type</span></span>|<span data-ttu-id="c11f4-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="c11f4-112">Retargeting</span></span>|
|<span data-ttu-id="c11f4-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c11f4-113">Affected APIs</span></span>|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

