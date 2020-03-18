---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803212"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="71c72-101">使用自定义 DataTemplates 时，在 ItemsControls（例如 ListBox 和 DataGrid）内间歇性无法滚动到底部项目</span><span class="sxs-lookup"><span data-stu-id="71c72-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71c72-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="71c72-102">Details</span></span>|<span data-ttu-id="71c72-103">在某些情况下，使用自定义 DataTemplates 时，.NET Framework 4.5 中的 bug 引起 ItemsControls（例如 <xref:System.Windows.Controls.ListBox?displayProperty=name>、<xref:System.Windows.Controls.ComboBox?displayProperty=name>、<xref:System.Windows.Controls.DataGrid?displayProperty=name> 等）无法滚动到底部项。</span><span class="sxs-lookup"><span data-stu-id="71c72-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="71c72-104">如果再次尝试滚动（在可重新滚动后），将可以滚动。</span><span class="sxs-lookup"><span data-stu-id="71c72-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>|
|<span data-ttu-id="71c72-105">建议</span><span class="sxs-lookup"><span data-stu-id="71c72-105">Suggestion</span></span>|<span data-ttu-id="71c72-106">此问题已在 .NET Framework 4.5.2 中解决，升级到该版本（或更高版本）的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="71c72-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="71c72-107">或者，用户仍可将滚动条拖动至这些集合中的最后几个项目，但可能需要尝试两次才能成功。</span><span class="sxs-lookup"><span data-stu-id="71c72-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>|
|<span data-ttu-id="71c72-108">范围</span><span class="sxs-lookup"><span data-stu-id="71c72-108">Scope</span></span>|<span data-ttu-id="71c72-109">次要</span><span class="sxs-lookup"><span data-stu-id="71c72-109">Minor</span></span>|
|<span data-ttu-id="71c72-110">Version</span><span class="sxs-lookup"><span data-stu-id="71c72-110">Version</span></span>|<span data-ttu-id="71c72-111">4.5</span><span class="sxs-lookup"><span data-stu-id="71c72-111">4.5</span></span>|
|<span data-ttu-id="71c72-112">类型</span><span class="sxs-lookup"><span data-stu-id="71c72-112">Type</span></span>|<span data-ttu-id="71c72-113">运行时</span><span class="sxs-lookup"><span data-stu-id="71c72-113">Runtime</span></span>|
