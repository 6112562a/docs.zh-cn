---
title: 在 UI 自动化中使用缓存
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: dd7506d388ba215f671ee3c7c4bae09baf4cc2b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040310"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="0802a-102">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="0802a-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="0802a-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="0802a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0802a-104">有关的最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 请[参阅 Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="0802a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0802a-105">本部分演示如何实现 <xref:System.Windows.Automation.AutomationElement> 属性和控件模式的缓存。</span><span class="sxs-lookup"><span data-stu-id="0802a-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="0802a-106">激活缓存请求</span><span class="sxs-lookup"><span data-stu-id="0802a-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="0802a-107">创建 <xref:System.Windows.Automation.CacheRequest>。</span><span class="sxs-lookup"><span data-stu-id="0802a-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="0802a-108">使用 <xref:System.Windows.Automation.CacheRequest.Add%2A>指定要缓存的属性和模式。</span><span class="sxs-lookup"><span data-stu-id="0802a-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="0802a-109">通过设置 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> 属性来指定缓存的范围。</span><span class="sxs-lookup"><span data-stu-id="0802a-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="0802a-110">通过设置 <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> 属性来指定子树视图。</span><span class="sxs-lookup"><span data-stu-id="0802a-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="0802a-111">如果想通过不检索对对象的完全引用来提高效率，请将 <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> 属性设置为 <xref:System.Windows.Automation.AutomationElementMode.None> 。</span><span class="sxs-lookup"><span data-stu-id="0802a-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="0802a-112">（这将导致无法从那些对象中检索当前值。）</span><span class="sxs-lookup"><span data-stu-id="0802a-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="0802a-113">使用<xref:System.Windows.Automation.CacheRequest.Activate%2A> 块`using`中的（`Using`在 Microsoft Visual Basic .net 中）激活请求。</span><span class="sxs-lookup"><span data-stu-id="0802a-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="0802a-114">在获得 <xref:System.Windows.Automation.AutomationElement> 对象或订阅事件后，通过使用 <xref:System.Windows.Automation.CacheRequest.Pop%2A> （如果使用了 <xref:System.Windows.Automation.CacheRequest.Push%2A> ）或处理 <xref:System.Windows.Automation.CacheRequest.Activate%2A>创建的对象来禁用请求。</span><span class="sxs-lookup"><span data-stu-id="0802a-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="0802a-115">（在<xref:System.Windows.Automation.CacheRequest.Activate%2A> Microsoft Visual Basic `using` .net`Using`中的块中使用。</span><span class="sxs-lookup"><span data-stu-id="0802a-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="0802a-116">缓存 AutomationElement 属性</span><span class="sxs-lookup"><span data-stu-id="0802a-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="0802a-117">当 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 获取 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>对象，或者获取 <xref:System.Windows.Automation.AutomationElement> 并将其作为 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时注册的事件的源。</span><span class="sxs-lookup"><span data-stu-id="0802a-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="0802a-118">（也可以通过下面的方法创建缓存：将 <xref:System.Windows.Automation.CacheRequest> 传递给 GetUpdatedCache 或 <xref:System.Windows.Automation.TreeWalker> 方法之一。）</span><span class="sxs-lookup"><span data-stu-id="0802a-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="0802a-119">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 或从 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 的 <xref:System.Windows.Automation.AutomationElement>属性中检索属性。</span><span class="sxs-lookup"><span data-stu-id="0802a-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="0802a-120">获取缓存模式及其属性</span><span class="sxs-lookup"><span data-stu-id="0802a-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="0802a-121">当 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 获取 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>对象，或者获取 <xref:System.Windows.Automation.AutomationElement> 并将其作为 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时注册的事件的源。</span><span class="sxs-lookup"><span data-stu-id="0802a-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="0802a-122">（也可以通过下面的方法创建缓存：将 <xref:System.Windows.Automation.CacheRequest> 传递给 GetUpdatedCache 或 <xref:System.Windows.Automation.TreeWalker> 方法之一。）</span><span class="sxs-lookup"><span data-stu-id="0802a-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="0802a-123">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> 检索缓存的模式。</span><span class="sxs-lookup"><span data-stu-id="0802a-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="0802a-124">控件模式的 `Cached` 属性中检索属性值。</span><span class="sxs-lookup"><span data-stu-id="0802a-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0802a-125">示例</span><span class="sxs-lookup"><span data-stu-id="0802a-125">Example</span></span>  
 <span data-ttu-id="0802a-126">下面的代码示例使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A> 激活 <xref:System.Windows.Automation.CacheRequest>，演示了缓存的各个方面。</span><span class="sxs-lookup"><span data-stu-id="0802a-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="0802a-127">示例</span><span class="sxs-lookup"><span data-stu-id="0802a-127">Example</span></span>  
 <span data-ttu-id="0802a-128">下面的代码示例使用 <xref:System.Windows.Automation.CacheRequest.Push%2A> 激活 <xref:System.Windows.Automation.CacheRequest>，演示了缓存的各个方面。</span><span class="sxs-lookup"><span data-stu-id="0802a-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="0802a-129">除非希望嵌套缓存请求，否则最好是使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A>。</span><span class="sxs-lookup"><span data-stu-id="0802a-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="0802a-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="0802a-130">See also</span></span>

- [<span data-ttu-id="0802a-131">在 UI 自动化客户端中缓存</span><span class="sxs-lookup"><span data-stu-id="0802a-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
