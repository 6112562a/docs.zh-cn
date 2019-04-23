---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803342"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="0559d-101">ETW 事件名称无法仅通过“Start”或“Stop”后缀区别开来</span><span class="sxs-lookup"><span data-stu-id="0559d-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0559d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0559d-102">Details</span></span>|<span data-ttu-id="0559d-103">在 .NET Framework 4.6 和 4.6.1 中，当两个 Windows 事件跟踪 (ETW) 事件名称只有 &quot;Start&quot; 或 &quot;Stop&quot; 后缀不同时（例如，当一个事件命名为 <code>LogUser</code>，另一个事件命名为 <code>LogUserStart</code>），运行时会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="0559d-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="0559d-104">在这种情况下，运行时不会构建不能发出任何日志记录的事件源。</span><span class="sxs-lookup"><span data-stu-id="0559d-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="0559d-105">建议</span><span class="sxs-lookup"><span data-stu-id="0559d-105">Suggestion</span></span>|<span data-ttu-id="0559d-106">若要避免此异常，请确保两个事件名称不是只有 &quot;Start&quot; 或 &quot;Stop&quot; 后缀不同。从 .NET Framework 4.6.2 开始，将删除此要求，运行时可区分只有 &quot;Start&quot; 和 &quot;Stop&quot; 后缀不同的事件名称。</span><span class="sxs-lookup"><span data-stu-id="0559d-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="0559d-107">范围</span><span class="sxs-lookup"><span data-stu-id="0559d-107">Scope</span></span>|<span data-ttu-id="0559d-108">边缘</span><span class="sxs-lookup"><span data-stu-id="0559d-108">Edge</span></span>|
|<span data-ttu-id="0559d-109">版本</span><span class="sxs-lookup"><span data-stu-id="0559d-109">Version</span></span>|<span data-ttu-id="0559d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="0559d-110">4.6</span></span>|
|<span data-ttu-id="0559d-111">类型</span><span class="sxs-lookup"><span data-stu-id="0559d-111">Type</span></span>|<span data-ttu-id="0559d-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="0559d-112">Retargeting</span></span>|
