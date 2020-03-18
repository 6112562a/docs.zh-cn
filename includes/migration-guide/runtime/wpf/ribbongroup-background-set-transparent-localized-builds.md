---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802481"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="adf23-101">本地化版本中的 RibbonGroup 背景设置为透明</span><span class="sxs-lookup"><span data-stu-id="adf23-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="adf23-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="adf23-102">Details</span></span>|<span data-ttu-id="adf23-103">始终用透明画笔绘制本地化版本上的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 背景，导致 UI 体验不佳。</span><span class="sxs-lookup"><span data-stu-id="adf23-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="adf23-104">.NET Framework 4.7 WPF 修复中通过更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 本地化资源修复了此问题，因而又确保会选中正确的画笔。</span><span class="sxs-lookup"><span data-stu-id="adf23-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="adf23-105">建议</span><span class="sxs-lookup"><span data-stu-id="adf23-105">Suggestion</span></span>|<span data-ttu-id="adf23-106">升级到 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="adf23-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="adf23-107">范围</span><span class="sxs-lookup"><span data-stu-id="adf23-107">Scope</span></span>|<span data-ttu-id="adf23-108">边缘</span><span class="sxs-lookup"><span data-stu-id="adf23-108">Edge</span></span>|
|<span data-ttu-id="adf23-109">Version</span><span class="sxs-lookup"><span data-stu-id="adf23-109">Version</span></span>|<span data-ttu-id="adf23-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="adf23-110">4.6.2</span></span>|
|<span data-ttu-id="adf23-111">类型</span><span class="sxs-lookup"><span data-stu-id="adf23-111">Type</span></span>|<span data-ttu-id="adf23-112">运行时</span><span class="sxs-lookup"><span data-stu-id="adf23-112">Runtime</span></span>|
