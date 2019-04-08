---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760415"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="6973f-101">在某些情况下工作流现在引发原始异常，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="6973f-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6973f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6973f-102">Details</span></span>|<span data-ttu-id="6973f-103">在 .NET Framework 4.6.2 和更低版本中，当工作流活动的 Execute 方法引发 <xref:System.Exception.Message> 属性 <code>null</code> 值的异常，那么 System.Activities 工作流运行时引发 <xref:System.NullReferenceException?displayProperty=name> 掩码原始异常。在 .NET Framework 4.7 中，引发之前掩码的异常。</span><span class="sxs-lookup"><span data-stu-id="6973f-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="6973f-104">建议</span><span class="sxs-lookup"><span data-stu-id="6973f-104">Suggestion</span></span>|<span data-ttu-id="6973f-105">如果你的代码依赖于处理 <xref:System.NullReferenceException?displayProperty=name>，请将其更改为捕获自定义活动可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="6973f-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="6973f-106">范围</span><span class="sxs-lookup"><span data-stu-id="6973f-106">Scope</span></span>|<span data-ttu-id="6973f-107">次要</span><span class="sxs-lookup"><span data-stu-id="6973f-107">Minor</span></span>|
|<span data-ttu-id="6973f-108">版本</span><span class="sxs-lookup"><span data-stu-id="6973f-108">Version</span></span>|<span data-ttu-id="6973f-109">4.7</span><span class="sxs-lookup"><span data-stu-id="6973f-109">4.7</span></span>|
|<span data-ttu-id="6973f-110">类型</span><span class="sxs-lookup"><span data-stu-id="6973f-110">Type</span></span>|<span data-ttu-id="6973f-111">运行时</span><span class="sxs-lookup"><span data-stu-id="6973f-111">Runtime</span></span>|
|<span data-ttu-id="6973f-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="6973f-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

