---
ms.openlocfilehash: 22c67c687f5581c181acc4aeab8910c4467fd424
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858453"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="c4d7d-101">在选定项目的 WPF ListBox、ListView 或 DataGrid 上调用 Items.Refresh 可能会导致元素中出现重复项目</span><span class="sxs-lookup"><span data-stu-id="c4d7d-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c4d7d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c4d7d-102">Details</span></span>|<span data-ttu-id="c4d7d-103">在 .NET Framework 4.5 中，在项目已在 <xref:System.Windows.Controls.ListBox?displayProperty=name> 中选定的同时从代码中调用 ListBox.Items.Refresh 可能会导致选定项目在列表中重复。</span><span class="sxs-lookup"><span data-stu-id="c4d7d-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=name> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="c4d7d-104"><xref:System.Windows.Controls.ListView?displayProperty=name> 和 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 会出现类似问题。</span><span class="sxs-lookup"><span data-stu-id="c4d7d-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=name> and <xref:System.Windows.Controls.DataGrid?displayProperty=name>.</span></span> <span data-ttu-id="c4d7d-105">此问题已在 .NET Framework 4.6 中解决。</span><span class="sxs-lookup"><span data-stu-id="c4d7d-105">This is fixed in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="c4d7d-106">建议</span><span class="sxs-lookup"><span data-stu-id="c4d7d-106">Suggestion</span></span>|<span data-ttu-id="c4d7d-107">在调用 <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> 前以编程方式取消选择项目，然后在调用完成后重新选择它们，可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="c4d7d-107">This issue may be worked around by programatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="c4d7d-108">此外，此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="c4d7d-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="c4d7d-109">范围</span><span class="sxs-lookup"><span data-stu-id="c4d7d-109">Scope</span></span>|<span data-ttu-id="c4d7d-110">次要</span><span class="sxs-lookup"><span data-stu-id="c4d7d-110">Minor</span></span>|
|<span data-ttu-id="c4d7d-111">版本</span><span class="sxs-lookup"><span data-stu-id="c4d7d-111">Version</span></span>|<span data-ttu-id="c4d7d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c4d7d-112">4.5</span></span>|
|<span data-ttu-id="c4d7d-113">类型</span><span class="sxs-lookup"><span data-stu-id="c4d7d-113">Type</span></span>|<span data-ttu-id="c4d7d-114">运行时</span><span class="sxs-lookup"><span data-stu-id="c4d7d-114">Runtime</span></span>|
|<span data-ttu-id="c4d7d-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c4d7d-115">Affected APIs</span></span>|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

