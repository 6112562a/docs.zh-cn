---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858492"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="0c24b-101">ETW EventListeners 无法从具有显式关键字的提供程序中（例如 TPL 提供程序）捕获事件</span><span class="sxs-lookup"><span data-stu-id="0c24b-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0c24b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0c24b-102">Details</span></span>|<span data-ttu-id="0c24b-103">具有空白关键字掩码的 ETW EventListeners 无法从具有显式关键字的提供程序中正确捕获事件。</span><span class="sxs-lookup"><span data-stu-id="0c24b-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="0c24b-104">在 .NET Framework 4.5 中，TPL 提供程序开始提供显式关键字，引发了此问题。</span><span class="sxs-lookup"><span data-stu-id="0c24b-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="0c24b-105">在 .NET Framework 4.6 中，EventListeners 已更新，此问题不再存在。</span><span class="sxs-lookup"><span data-stu-id="0c24b-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>|
|<span data-ttu-id="0c24b-106">建议</span><span class="sxs-lookup"><span data-stu-id="0c24b-106">Suggestion</span></span>|<span data-ttu-id="0c24b-107">要解决此问题，请将对 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的调用替换为 EnableEvents 重载，以显式指定要使用的“任意关键字”掩码：<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="0c24b-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="0c24b-108">范围</span><span class="sxs-lookup"><span data-stu-id="0c24b-108">Scope</span></span>|<span data-ttu-id="0c24b-109">边缘</span><span class="sxs-lookup"><span data-stu-id="0c24b-109">Edge</span></span>|
|<span data-ttu-id="0c24b-110">版本</span><span class="sxs-lookup"><span data-stu-id="0c24b-110">Version</span></span>|<span data-ttu-id="0c24b-111">4.5</span><span class="sxs-lookup"><span data-stu-id="0c24b-111">4.5</span></span>|
|<span data-ttu-id="0c24b-112">类型</span><span class="sxs-lookup"><span data-stu-id="0c24b-112">Type</span></span>|<span data-ttu-id="0c24b-113">运行时</span><span class="sxs-lookup"><span data-stu-id="0c24b-113">Runtime</span></span>|
|<span data-ttu-id="0c24b-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0c24b-114">Affected APIs</span></span>|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

