---
title: 实现 UI 自动化 MultipleView 控件模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 26e8ae7d0c560d8539b17e29d47545894cb4bb0f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545199"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="5e1d0-102">实现 UI 自动化 MultipleView 控件模式</span><span class="sxs-lookup"><span data-stu-id="5e1d0-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5e1d0-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5e1d0-104">有关的最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 请[参阅 Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5e1d0-105">本主题介绍了实现 <xref:System.Windows.Automation.Provider.IMultipleViewProvider>的准则和约定，包括有关事件和属性的信息。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="5e1d0-106">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5e1d0-107"><xref:System.Windows.Automation.MultipleViewPattern> 控件模式用于支持那些提供并能够在同组信息或子控件的多个表示形式间进行切换的控件。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="5e1d0-108">可显示多个视图的控件示例包括列表视图 (可将其内容显示为缩略图、磁贴、图标或详细信息) [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] 、图表 (饼图、折线图、条形图、带有公式的单元值[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] )、文档 (常规、Web 版式、打印布局、阅读版式、大纲)、Microsoft Outlook 日历 (年、月、周、天) 和[!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)]外观。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="5e1d0-109">支持的视图由控件开发人员确定，并特定于每个控件。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5e1d0-110">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="5e1d0-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5e1d0-111">在实现 Multiple View 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="5e1d0-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5e1d0-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> 还应在一个容器中实现，此容器用于管理当前视图，如果它不同于提供当前视图的控件。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="5e1d0-113">例如，Windows 资源管理器包含当前文件夹内容的列表控件，而该控件的视图是从 Windows 资源管理器应用程序进行管理的。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="5e1d0-114">能够对其内容进行排序的控件不被视为支持多个视图。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="5e1d0-115">视图的集合必须跨实例相同。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="5e1d0-116">视图名称必须是适合在文本到语音转换、盲文和其他用户可读的应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="5e1d0-117">IMultipleViewProvider 所需的成员</span><span class="sxs-lookup"><span data-stu-id="5e1d0-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="5e1d0-118">实现 IMultipleViewProvider 需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="5e1d0-119">必需的成员</span><span class="sxs-lookup"><span data-stu-id="5e1d0-119">Required members</span></span>|<span data-ttu-id="5e1d0-120">成员类型</span><span class="sxs-lookup"><span data-stu-id="5e1d0-120">Member type</span></span>|<span data-ttu-id="5e1d0-121">说明</span><span class="sxs-lookup"><span data-stu-id="5e1d0-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="5e1d0-122">Property</span><span class="sxs-lookup"><span data-stu-id="5e1d0-122">Property</span></span>|<span data-ttu-id="5e1d0-123">无</span><span class="sxs-lookup"><span data-stu-id="5e1d0-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="5e1d0-124">方法</span><span class="sxs-lookup"><span data-stu-id="5e1d0-124">Method</span></span>|<span data-ttu-id="5e1d0-125">无</span><span class="sxs-lookup"><span data-stu-id="5e1d0-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="5e1d0-126">方法</span><span class="sxs-lookup"><span data-stu-id="5e1d0-126">Method</span></span>|<span data-ttu-id="5e1d0-127">无</span><span class="sxs-lookup"><span data-stu-id="5e1d0-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="5e1d0-128">方法</span><span class="sxs-lookup"><span data-stu-id="5e1d0-128">Method</span></span>|<span data-ttu-id="5e1d0-129">无</span><span class="sxs-lookup"><span data-stu-id="5e1d0-129">None</span></span>|  
  
 <span data-ttu-id="5e1d0-130">没有与此控件模式相关联的事件。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5e1d0-131">Exceptions</span><span class="sxs-lookup"><span data-stu-id="5e1d0-131">Exceptions</span></span>  
 <span data-ttu-id="5e1d0-132">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5e1d0-133">异常类型</span><span class="sxs-lookup"><span data-stu-id="5e1d0-133">Exception type</span></span>|<span data-ttu-id="5e1d0-134">条件</span><span class="sxs-lookup"><span data-stu-id="5e1d0-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="5e1d0-135">当 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> 或 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> 与不是受支持视图集合成员的参数一同被调用时。</span><span class="sxs-lookup"><span data-stu-id="5e1d0-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e1d0-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="5e1d0-136">See also</span></span>

- [<span data-ttu-id="5e1d0-137">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="5e1d0-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5e1d0-138">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="5e1d0-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5e1d0-139">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="5e1d0-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5e1d0-140">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="5e1d0-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="5e1d0-141">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="5e1d0-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
