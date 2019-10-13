---
title: 使用 AutomationID 属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 7a172db8bcb626d78a24b546147b4e32f20f5d83
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291341"
---
# <a name="use-the-automationid-property"></a><span data-ttu-id="bdc96-102">使用 AutomationID 属性</span><span class="sxs-lookup"><span data-stu-id="bdc96-102">Use the AutomationID Property</span></span>
> [!NOTE]
> <span data-ttu-id="bdc96-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="bdc96-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bdc96-104">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新信息，请参阅 @no__t 1Windows 自动化 API：UI Automation @ no__t。</span><span class="sxs-lookup"><span data-stu-id="bdc96-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bdc96-105">本主题包含一些方案和代码示例，这些方案和代码示例演示如何以及在何时能够使用 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树中找到元素。</span><span class="sxs-lookup"><span data-stu-id="bdc96-105">This topic contains scenarios and sample code that show how and when the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> can be used to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>  
  
 <span data-ttu-id="bdc96-106"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 唯一地将 UI 自动化元素从其同级中标识出来。</span><span class="sxs-lookup"><span data-stu-id="bdc96-106"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> uniquely identifies a UI Automation element from its siblings.</span></span> <span data-ttu-id="bdc96-107">有关与控件标识相关的属性标识符的详细信息，请参阅 [UI Automation Properties Overview](ui-automation-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bdc96-107">For more information on property identifiers related to control identification, see [UI Automation Properties Overview](ui-automation-properties-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdc96-108"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 不保证标识在整个树中的唯一性；它通常需要容器和范围信息才有用。</span><span class="sxs-lookup"><span data-stu-id="bdc96-108"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> does not guarantee a unique identity throughout the tree; it typically needs container and scope information to be useful.</span></span> <span data-ttu-id="bdc96-109">例如，一个应用程序可能包含具有多个顶级菜单项的菜单控件，而这些顶级菜单项又具有多个子菜单项。</span><span class="sxs-lookup"><span data-stu-id="bdc96-109">For example, an application may contain a menu control with multiple top-level menu items that, in turn, have multiple child menu items.</span></span> <span data-ttu-id="bdc96-110">这些二级菜单项通过常规架构（如“Item1”、“Item2”，依此类推）进行标识，允许对顶级菜单项中的子菜单项使用重复的标识符。</span><span class="sxs-lookup"><span data-stu-id="bdc96-110">These secondary menu items may be identified by a generic scheme such as "Item1", "Item 2", and so on, allowing duplicate identifiers for children across top-level menu items.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="bdc96-111">方案</span><span class="sxs-lookup"><span data-stu-id="bdc96-111">Scenarios</span></span>  
 <span data-ttu-id="bdc96-112">已确定有三个主要的 UI 自动化客户端应用程序方案需要使用 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 才能在搜索元素时获得准确一致的结果。</span><span class="sxs-lookup"><span data-stu-id="bdc96-112">Three primary UI Automation client application scenarios have been identified that require the use of <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> to achieve accurate and consistent results when searching for elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdc96-113">控件视图中（除顶级应用程序窗口外）的所有 UI 自动化元素、派生自没有 ID 或 x:Uid 的<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 控件的 UI 自动化元素以及派生自没有控件 ID 的 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控件的 UI 自动化元素都支持 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bdc96-113"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> is supported by all UI Automation elements in the control view except top-level application windows, UI Automation elements derived from [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls that do not have an ID or x:Uid, and UI Automation elements derived from [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] controls that do not have a control ID.</span></span>  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a><span data-ttu-id="bdc96-114">使用唯一且可发现的 AutomationID 在 UI 自动化树中查找特定元素</span><span class="sxs-lookup"><span data-stu-id="bdc96-114">Use a unique and discoverable AutomationID to locate a specific element in the UI Automation tree</span></span>  
  
- <span data-ttu-id="bdc96-115">使用工具（如 UI Spy）报告感兴趣的 @no__t 元素的 @no__t。</span><span class="sxs-lookup"><span data-stu-id="bdc96-115">Use a tool such as UI Spy to report the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> of a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element of interest.</span></span> <span data-ttu-id="bdc96-116">然后，可以将此值复制并粘贴到客户端应用程序（如测试脚本）中，以便随后进行自动化测试。</span><span class="sxs-lookup"><span data-stu-id="bdc96-116">This value can then be copied and pasted into a client application such as a test script for subsequent automated testing.</span></span> <span data-ttu-id="bdc96-117">此方法减少并简化了在运行时标识和查找元素所需的代码。</span><span class="sxs-lookup"><span data-stu-id="bdc96-117">This approach reduces and simplifies the code necessary to identify and locate an element at runtime.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="bdc96-118">通常，你应当尝试只获取 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>的直接子项。</span><span class="sxs-lookup"><span data-stu-id="bdc96-118">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="bdc96-119">对后代的搜索可能循环访问数百个甚至数千个元素，这可能导致堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="bdc96-119">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="bdc96-120">如果尝试在较低级别上获取特定元素，应该从应用程序窗口或者从较低级别的容器中开始搜索。</span><span class="sxs-lookup"><span data-stu-id="bdc96-120">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="bdc96-121">使用持久的路径返回到之前标识的 AutomationElement</span><span class="sxs-lookup"><span data-stu-id="bdc96-121">Use a persistent path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="bdc96-122">客户端应用程序（从简单的测试脚本到强大的录制和播放实用程序）可能需要访问当前未实例化并因此不存在于 UI 自动化树中的元素（如打开文件对话框或菜单项）。</span><span class="sxs-lookup"><span data-stu-id="bdc96-122">Client applications, from simple test scripts to robust record and playback utilities, may require access to elements that are not currently instantiated, such as a file open dialog or a menu item and therefore do not exist in the UI Automation tree.</span></span> <span data-ttu-id="bdc96-123">只有通过使用 UI 自动化属性（如 AutomationID、控件模式和事件侦听器），才能通过复制或 "播放" 来实例化这些元素。</span><span class="sxs-lookup"><span data-stu-id="bdc96-123">These elements can only be instantiated by reproducing, or "playing back", a specific sequence of UI actions through the use of UI Automation properties such as AutomationID, control patterns, and event listeners.</span></span>
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="bdc96-124">使用相对路径返回到之前标识的 AutomationElement</span><span class="sxs-lookup"><span data-stu-id="bdc96-124">Use a relative path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="bdc96-125">在某些情况下，由于只能保证 AutomationID 在同级项之间唯一，因此 UI 自动化树中的多个元素可能具有相同的 AutomationID 属性值。</span><span class="sxs-lookup"><span data-stu-id="bdc96-125">In certain circumstances, since AutomationID is only guaranteed to be unique amongst siblings, multiple elements in the UI Automation tree may have identical AutomationID property values.</span></span> <span data-ttu-id="bdc96-126">对于这些情况，可以基于父项（必要情况下使用其祖父项）来唯一地标识元素。</span><span class="sxs-lookup"><span data-stu-id="bdc96-126">In these situations the elements can be uniquely identified based on a parent and, if necessary, a grandparent.</span></span> <span data-ttu-id="bdc96-127">例如，开发人员可能提供一个包含多个菜单项（其中每个菜单项又包含多个子菜单项）的菜单栏，其中的子项是用连续的 AutomationID（如“Item1”、“Item2”，依此类推）标识的。</span><span class="sxs-lookup"><span data-stu-id="bdc96-127">For example, a developer may provide a menu bar with multiple menu items each with multiple child menu items where the children are identified with sequential AutomationID's such as "Item1", "Item2", and so on.</span></span> <span data-ttu-id="bdc96-128">然后，可以通过其 AutomationID 以及其父项（必要情况下使用其祖父项）的 AutomationID 来唯一地标识每个菜单项。</span><span class="sxs-lookup"><span data-stu-id="bdc96-128">Each menu item could then be uniquely identified by its AutomationID along with the AutomationID of its parent and, if necessary, its grandparent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc96-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdc96-129">See also</span></span>

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [<span data-ttu-id="bdc96-130">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="bdc96-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bdc96-131">基于属性条件查找 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="bdc96-131">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
