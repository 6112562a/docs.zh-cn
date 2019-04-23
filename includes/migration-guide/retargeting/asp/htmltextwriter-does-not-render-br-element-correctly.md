---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803373"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="4168f-101">HtmlTextWriter 未正确呈现 `<br/>` 元素</span><span class="sxs-lookup"><span data-stu-id="4168f-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4168f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4168f-102">Details</span></span>|<span data-ttu-id="4168f-103">从 .NET Framework 4.6 开始，调用带有 <code>&lt;BR /&gt;</code> 的 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 将正确插入唯一 <code>&lt;BR /&gt;</code>（而非两个）</span><span class="sxs-lookup"><span data-stu-id="4168f-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="4168f-104">建议</span><span class="sxs-lookup"><span data-stu-id="4168f-104">Suggestion</span></span>|<span data-ttu-id="4168f-105">如果应用依赖于多余的 <code>&lt;BR /&gt;</code> 标记，应再次调用 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="4168f-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="4168f-106">请注意，此行为更改仅影响面向 .NET Framework 4.6 或更高版本的应用，因此另一选项是面向以前版本的 .NET Framework 以便获取旧行为。</span><span class="sxs-lookup"><span data-stu-id="4168f-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="4168f-107">范围</span><span class="sxs-lookup"><span data-stu-id="4168f-107">Scope</span></span>|<span data-ttu-id="4168f-108">边缘</span><span class="sxs-lookup"><span data-stu-id="4168f-108">Edge</span></span>|
|<span data-ttu-id="4168f-109">版本</span><span class="sxs-lookup"><span data-stu-id="4168f-109">Version</span></span>|<span data-ttu-id="4168f-110">4.6</span><span class="sxs-lookup"><span data-stu-id="4168f-110">4.6</span></span>|
|<span data-ttu-id="4168f-111">类型</span><span class="sxs-lookup"><span data-stu-id="4168f-111">Type</span></span>|<span data-ttu-id="4168f-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="4168f-112">Retargeting</span></span>|
|<span data-ttu-id="4168f-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4168f-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
