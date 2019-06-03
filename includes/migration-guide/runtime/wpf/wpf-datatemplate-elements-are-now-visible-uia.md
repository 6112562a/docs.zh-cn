---
ms.openlocfilehash: 51691ced3f05201f784ccdeffbc130e34748b7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379512"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="a5f7a-101">WPF DataTemplate 元素现在对 UIA 可见</span><span class="sxs-lookup"><span data-stu-id="a5f7a-101">WPF DataTemplate elements are now visible to UIA</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a5f7a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a5f7a-102">Details</span></span>|<span data-ttu-id="a5f7a-103">以前 <xref:System.Windows.DataTemplate?displayProperty=name> 元素对 UI 自动化不可见。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=name> elements were invisible to UI Automation.</span></span> <span data-ttu-id="a5f7a-104">从 4.5 开始，UI 自动化将能检测到这些元素。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="a5f7a-105">这在许多情况下很有用，但可能会中断依赖于不包含 <xref:System.Windows.DataTemplate?displayProperty=name> 元素的 UIA 树的测试。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=name> elements.</span></span>|
|<span data-ttu-id="a5f7a-106">建议</span><span class="sxs-lookup"><span data-stu-id="a5f7a-106">Suggestion</span></span>|<span data-ttu-id="a5f7a-107">此应用的 UI 自动化测试需要更新，以便考虑到 UIA 树现在所包含的以前不可见的 <xref:System.Windows.DataTemplate?displayProperty=name> 元素。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=name> elements.</span></span> <span data-ttu-id="a5f7a-108">例如，对于预计某些元素彼此相邻的测试，现在需要考虑到其间之前不可见的 UIA 元素。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="a5f7a-109">否则，依赖 UIA 元素的特定计数或索引的测试可能需要使用新值进行更新。</span><span class="sxs-lookup"><span data-stu-id="a5f7a-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>|
|<span data-ttu-id="a5f7a-110">范围</span><span class="sxs-lookup"><span data-stu-id="a5f7a-110">Scope</span></span>|<span data-ttu-id="a5f7a-111">边缘</span><span class="sxs-lookup"><span data-stu-id="a5f7a-111">Edge</span></span>|
|<span data-ttu-id="a5f7a-112">版本</span><span class="sxs-lookup"><span data-stu-id="a5f7a-112">Version</span></span>|<span data-ttu-id="a5f7a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a5f7a-113">4.5</span></span>|
|<span data-ttu-id="a5f7a-114">类型</span><span class="sxs-lookup"><span data-stu-id="a5f7a-114">Type</span></span>|<span data-ttu-id="a5f7a-115">运行时</span><span class="sxs-lookup"><span data-stu-id="a5f7a-115">Runtime</span></span>|
|<span data-ttu-id="a5f7a-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a5f7a-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
