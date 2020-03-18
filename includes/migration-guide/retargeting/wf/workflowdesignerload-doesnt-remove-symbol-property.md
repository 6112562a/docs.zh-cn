---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804654"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="f1ee0-101">WorkflowDesigner.Load 不会删除符号属性</span><span class="sxs-lookup"><span data-stu-id="f1ee0-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f1ee0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f1ee0-102">Details</span></span>|<span data-ttu-id="f1ee0-103">当在工作流设计器中面向 .NET Framework 4.5，并使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法加载重新托管的 3.5 工作流时，保存该工作流的同时将引发 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="f1ee0-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="f1ee0-104">建议</span><span class="sxs-lookup"><span data-stu-id="f1ee0-104">Suggestion</span></span>|<span data-ttu-id="f1ee0-105">此 bug 仅当在工作流设计器中面向 .NET Framework 4.5 时才显示，因此可通过将 <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 设为 4.0 .NET Framework 进行解决。或者，可使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法而非 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法加载工作流来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="f1ee0-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="f1ee0-106">范围</span><span class="sxs-lookup"><span data-stu-id="f1ee0-106">Scope</span></span>|<span data-ttu-id="f1ee0-107">主要</span><span class="sxs-lookup"><span data-stu-id="f1ee0-107">Major</span></span>|
|<span data-ttu-id="f1ee0-108">Version</span><span class="sxs-lookup"><span data-stu-id="f1ee0-108">Version</span></span>|<span data-ttu-id="f1ee0-109">4.5</span><span class="sxs-lookup"><span data-stu-id="f1ee0-109">4.5</span></span>|
|<span data-ttu-id="f1ee0-110">类型</span><span class="sxs-lookup"><span data-stu-id="f1ee0-110">Type</span></span>|<span data-ttu-id="f1ee0-111">重定目标</span><span class="sxs-lookup"><span data-stu-id="f1ee0-111">Retargeting</span></span>|
|<span data-ttu-id="f1ee0-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f1ee0-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
