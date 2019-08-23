---
title: 实现 UI 自动化 Grid 控件模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 5eceafee4d02478c9e011a473ee1d036df91075d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932185"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="21613-102">实现 UI 自动化 Grid 控件模式</span><span class="sxs-lookup"><span data-stu-id="21613-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="21613-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="21613-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="21613-104">有关的最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 请[参阅 Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="21613-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="21613-105">本主题介绍实现 <xref:System.Windows.Automation.Provider.IGridProvider>的准则和约定，包括有关属性、方法和事件的信息。</span><span class="sxs-lookup"><span data-stu-id="21613-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="21613-106">本概述的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="21613-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="21613-107"><xref:System.Windows.Automation.GridPattern> 控件模式用于支持作为子元素集合的容器的控件。</span><span class="sxs-lookup"><span data-stu-id="21613-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="21613-108">此元素的子元素必须实现 <xref:System.Windows.Automation.Provider.IGridItemProvider> ，并且在可以按行和列进行遍历的二维逻辑坐标系统中进行组织。</span><span class="sxs-lookup"><span data-stu-id="21613-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="21613-109">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="21613-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="21613-110">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="21613-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="21613-111">在实现 Grid 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="21613-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="21613-112">网格坐标从零开始，左上角单元格（或右上角单元格，具体取决于区域设置）的坐标为 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="21613-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="21613-113">如果某个单元格为空，必须仍返回 UI 自动化元素以便支持该单元格的 <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="21613-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="21613-114">当网格中的子元素的布局类似于未对齐的数组时，这是可能的（请参阅下面的示例）。</span><span class="sxs-lookup"><span data-stu-id="21613-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="21613-115">![显示不规则布局的 Windows 资源管理器视图。](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="21613-115">![Windows Explorer view showing ragged layout.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="21613-116">坐标为空的 Grid 控件的示例</span><span class="sxs-lookup"><span data-stu-id="21613-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="21613-117">只有一项的网格仍需要实现 <xref:System.Windows.Automation.Provider.IGridProvider> （如果它逻辑上被视为网格）。</span><span class="sxs-lookup"><span data-stu-id="21613-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="21613-118">网格中的子项数并不重要。</span><span class="sxs-lookup"><span data-stu-id="21613-118">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="21613-119">隐藏的行和列（具体取决于提供程序实现）可能会在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树中加载，因此将会反映在 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> 和 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> 属性中。</span><span class="sxs-lookup"><span data-stu-id="21613-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="21613-120">如果尚未加载隐藏的行和列，则不应对它们进行计数。</span><span class="sxs-lookup"><span data-stu-id="21613-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="21613-121"><xref:System.Windows.Automation.Provider.IGridProvider> 不会启用网格的主动操作；必须实现 <xref:System.Windows.Automation.Provider.ITransformProvider> 以启用此功能。</span><span class="sxs-lookup"><span data-stu-id="21613-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="21613-122">使用 <xref:System.Windows.Automation.StructureChangedEventHandler> 来侦听对网格的结构和布局更改（如已添加、删除或合并的单元格）。</span><span class="sxs-lookup"><span data-stu-id="21613-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="21613-123">使用 <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> 来跟踪遍历的网格的项或单元格。</span><span class="sxs-lookup"><span data-stu-id="21613-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="21613-124">IGridProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="21613-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="21613-125">实现 IGridProvider 接口需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="21613-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="21613-126">必需的成员</span><span class="sxs-lookup"><span data-stu-id="21613-126">Required members</span></span>|<span data-ttu-id="21613-127">类型</span><span class="sxs-lookup"><span data-stu-id="21613-127">Type</span></span>|<span data-ttu-id="21613-128">说明</span><span class="sxs-lookup"><span data-stu-id="21613-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="21613-129">Property</span><span class="sxs-lookup"><span data-stu-id="21613-129">Property</span></span>|<span data-ttu-id="21613-130">无</span><span class="sxs-lookup"><span data-stu-id="21613-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="21613-131">Property</span><span class="sxs-lookup"><span data-stu-id="21613-131">Property</span></span>|<span data-ttu-id="21613-132">无</span><span class="sxs-lookup"><span data-stu-id="21613-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="21613-133">方法</span><span class="sxs-lookup"><span data-stu-id="21613-133">Method</span></span>|<span data-ttu-id="21613-134">无</span><span class="sxs-lookup"><span data-stu-id="21613-134">None</span></span>|  
  
 <span data-ttu-id="21613-135">没有与此控件模式关联的事件。</span><span class="sxs-lookup"><span data-stu-id="21613-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="21613-136">Exceptions</span><span class="sxs-lookup"><span data-stu-id="21613-136">Exceptions</span></span>  
 <span data-ttu-id="21613-137">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="21613-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="21613-138">异常类型</span><span class="sxs-lookup"><span data-stu-id="21613-138">Exception type</span></span>|<span data-ttu-id="21613-139">条件</span><span class="sxs-lookup"><span data-stu-id="21613-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="21613-140">-如果请求的行坐标<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>大于或列坐标大于, <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>则为。</span><span class="sxs-lookup"><span data-stu-id="21613-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="21613-141">-如果请求的行坐标或列坐标都小于零。</span><span class="sxs-lookup"><span data-stu-id="21613-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21613-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="21613-142">See also</span></span>

- [<span data-ttu-id="21613-143">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="21613-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="21613-144">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="21613-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="21613-145">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="21613-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="21613-146">实现 UI 自动化 GridItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="21613-146">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="21613-147">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="21613-147">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="21613-148">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="21613-148">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
