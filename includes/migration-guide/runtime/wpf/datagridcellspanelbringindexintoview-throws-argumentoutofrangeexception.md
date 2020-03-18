---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802472"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="c09a6-101">DataGridCellsPanel.BringIndexIntoView 引发 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="c09a6-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c09a6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c09a6-102">Details</span></span>|<span data-ttu-id="c09a6-103">启用列虚拟化但尚未确定列宽时，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 将以异步方式执行工作。</span><span class="sxs-lookup"><span data-stu-id="c09a6-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="c09a6-104">如果在异步工作执行之前删除列，可能会出现 <xref:System.ArgumentOutOfRangeException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="c09a6-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=name> can occur.</span></span>|
|<span data-ttu-id="c09a6-105">建议</span><span class="sxs-lookup"><span data-stu-id="c09a6-105">Suggestion</span></span>|<span data-ttu-id="c09a6-106">以下任一项：</span><span class="sxs-lookup"><span data-stu-id="c09a6-106">Any one of the following:</span></span><ol><li><span data-ttu-id="c09a6-107">升级到 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="c09a6-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="c09a6-108">安装 .NET Framework 4.6.2 的最新服务修补程序。</span><span class="sxs-lookup"><span data-stu-id="c09a6-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="c09a6-109">在对 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的异步响应完成前，避免删除列。</span><span class="sxs-lookup"><span data-stu-id="c09a6-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>|
|<span data-ttu-id="c09a6-110">范围</span><span class="sxs-lookup"><span data-stu-id="c09a6-110">Scope</span></span>|<span data-ttu-id="c09a6-111">边缘</span><span class="sxs-lookup"><span data-stu-id="c09a6-111">Edge</span></span>|
|<span data-ttu-id="c09a6-112">Version</span><span class="sxs-lookup"><span data-stu-id="c09a6-112">Version</span></span>|<span data-ttu-id="c09a6-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c09a6-113">4.6.2</span></span>|
|<span data-ttu-id="c09a6-114">类型</span><span class="sxs-lookup"><span data-stu-id="c09a6-114">Type</span></span>|<span data-ttu-id="c09a6-115">运行时</span><span class="sxs-lookup"><span data-stu-id="c09a6-115">Runtime</span></span>|
|<span data-ttu-id="c09a6-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c09a6-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
