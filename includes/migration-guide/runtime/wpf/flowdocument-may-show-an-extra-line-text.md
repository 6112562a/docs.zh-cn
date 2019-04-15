---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235077"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="9617e-101">FlowDocument 可能显示额外的文本行</span><span class="sxs-lookup"><span data-stu-id="9617e-101">FlowDocument may show an extra line of text</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9617e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9617e-102">Details</span></span>|<span data-ttu-id="9617e-103">在某些情况下，当 <xref:System.Windows.Documents.FlowDocument> 元素在 .NET Framework 4.5 上运行时，可能显示额外的文本行，这是与它在 .NET Framework 4.0 上运行时显示的不同之处。</span><span class="sxs-lookup"><span data-stu-id="9617e-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="9617e-104">暂未出现已知的案例显示此更改导致任意文本难以阅读或显示不明，但是它可能导致出现之前 <xref:System.Windows.Documents.FlowDocument> 视图中忽略的文本。</span><span class="sxs-lookup"><span data-stu-id="9617e-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>|
|<span data-ttu-id="9617e-105">建议</span><span class="sxs-lookup"><span data-stu-id="9617e-105">Suggestion</span></span>|<span data-ttu-id="9617e-106">在某些情况下，减少一个显示元素的 PageHeight 属性可能还原之前显示的行数。</span><span class="sxs-lookup"><span data-stu-id="9617e-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>|
|<span data-ttu-id="9617e-107">范围</span><span class="sxs-lookup"><span data-stu-id="9617e-107">Scope</span></span>|<span data-ttu-id="9617e-108">边缘</span><span class="sxs-lookup"><span data-stu-id="9617e-108">Edge</span></span>|
|<span data-ttu-id="9617e-109">版本</span><span class="sxs-lookup"><span data-stu-id="9617e-109">Version</span></span>|<span data-ttu-id="9617e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="9617e-110">4.5</span></span>|
|<span data-ttu-id="9617e-111">类型</span><span class="sxs-lookup"><span data-stu-id="9617e-111">Type</span></span>|<span data-ttu-id="9617e-112">运行时</span><span class="sxs-lookup"><span data-stu-id="9617e-112">Runtime</span></span>|
|<span data-ttu-id="9617e-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9617e-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|
