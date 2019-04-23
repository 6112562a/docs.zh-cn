---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774129"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="6cdf4-101">默认应用域的 TargetFrameworkName 不再默认为 null（如果未设置）</span><span class="sxs-lookup"><span data-stu-id="6cdf4-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6cdf4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6cdf4-102">Details</span></span>|<span data-ttu-id="6cdf4-103">以前，除非显式设置，否则默认应用域中的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 为 null。</span><span class="sxs-lookup"><span data-stu-id="6cdf4-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="6cdf4-104">从 4.6 开始，默认应用域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 属性将具有派生自 TargetFrameworkAttribute 的默认值（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="6cdf4-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="6cdf4-105">除非显式重写，否则非默认应用域将继续从默认应用域继承 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name>（在 4.6 中不会默认为 null）。</span><span class="sxs-lookup"><span data-stu-id="6cdf4-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>|
|<span data-ttu-id="6cdf4-106">建议</span><span class="sxs-lookup"><span data-stu-id="6cdf4-106">Suggestion</span></span>|<span data-ttu-id="6cdf4-107">应更新代码，以独立于默认为 null 的 <xref:System.AppDomainSetup.TargetFrameworkName>。</span><span class="sxs-lookup"><span data-stu-id="6cdf4-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="6cdf4-108">如果需要此属性继续评估为 null，它可显式设为该值。</span><span class="sxs-lookup"><span data-stu-id="6cdf4-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>|
|<span data-ttu-id="6cdf4-109">范围</span><span class="sxs-lookup"><span data-stu-id="6cdf4-109">Scope</span></span>|<span data-ttu-id="6cdf4-110">边缘</span><span class="sxs-lookup"><span data-stu-id="6cdf4-110">Edge</span></span>|
|<span data-ttu-id="6cdf4-111">版本</span><span class="sxs-lookup"><span data-stu-id="6cdf4-111">Version</span></span>|<span data-ttu-id="6cdf4-112">4.6</span><span class="sxs-lookup"><span data-stu-id="6cdf4-112">4.6</span></span>|
|<span data-ttu-id="6cdf4-113">类型</span><span class="sxs-lookup"><span data-stu-id="6cdf4-113">Type</span></span>|<span data-ttu-id="6cdf4-114">运行时</span><span class="sxs-lookup"><span data-stu-id="6cdf4-114">Runtime</span></span>|
|<span data-ttu-id="6cdf4-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="6cdf4-115">Affected APIs</span></span>|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
