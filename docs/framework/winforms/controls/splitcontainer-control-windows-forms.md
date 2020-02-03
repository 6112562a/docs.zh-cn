---
title: SplitContainer 控件
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742904"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="90d58-102">SplitContainer 控件（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="90d58-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="90d58-103">Windows 窗体 `SplitContainer` 控件可视为一个复合控件；它是由可移动条隔开的两个面板。</span><span class="sxs-lookup"><span data-stu-id="90d58-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="90d58-104">当鼠标指针位于条上方时，指针将改变形状以表示条可移动。</span><span class="sxs-lookup"><span data-stu-id="90d58-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90d58-105">在 "**工具箱**" 中，此控件替换 Visual Studio 早期版本中的 <xref:System.Windows.Forms.Splitter> 控件。</span><span class="sxs-lookup"><span data-stu-id="90d58-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="90d58-106">相较于 `SplitContainer` 控件，优先选择 <xref:System.Windows.Forms.Splitter> 控件。</span><span class="sxs-lookup"><span data-stu-id="90d58-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="90d58-107"><xref:System.Windows.Forms.Splitter> 类仍包含在 .NET Framework 中，以便与现有应用程序兼容，但我们强烈建议为新项目使用 `SplitContainer` 控件。</span><span class="sxs-lookup"><span data-stu-id="90d58-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="90d58-108">`SplitContainer` 控件允许你创建复杂的用户界面；通常情况下，在一个面板中的选择将决定显示在另一个面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="90d58-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="90d58-109">这种安排对于显示和浏览信息非常有效。</span><span class="sxs-lookup"><span data-stu-id="90d58-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="90d58-110">拥有两个面板使你能够在区域、条或“拆分器”中聚合信息，使用户可轻松地调整面板大小。</span><span class="sxs-lookup"><span data-stu-id="90d58-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90d58-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="90d58-111">In This Section</span></span>  
 [<span data-ttu-id="90d58-112">SplitContainer 控件概述</span><span class="sxs-lookup"><span data-stu-id="90d58-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="90d58-113">介绍 `SplitContainer` 控件并描述常用的属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="90d58-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="90d58-114">如何：定义拆分窗口中的重设大小和定位行为</span><span class="sxs-lookup"><span data-stu-id="90d58-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="90d58-115">描述如何在 `SplitContainer` 控件中控制拆分器。</span><span class="sxs-lookup"><span data-stu-id="90d58-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="90d58-116">如何：水平拆分窗口</span><span class="sxs-lookup"><span data-stu-id="90d58-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="90d58-117">描述如何在 `SplitContainer` 控件中控制拆分器的方向。</span><span class="sxs-lookup"><span data-stu-id="90d58-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="90d58-118">如何：使用 Windows 窗体创建多窗格用户界面</span><span class="sxs-lookup"><span data-stu-id="90d58-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="90d58-119">创建一个与 Microsoft Outlook 中使用的多窗格用户界面相似的多窗格用户界面。</span><span class="sxs-lookup"><span data-stu-id="90d58-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="90d58-120">另请参阅[如何：使用设计器水平拆分窗口](how-to-split-a-window-horizontally-using-the-designer.md)，[如何：在 windows 窗体上创建 Windows 资源管理器样式的界面](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)，[如何：使用设计器 Windows 窗体创建多窗格用户界面](create-a-multipane-user-interface-with-wf-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="90d58-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90d58-121">参考</span><span class="sxs-lookup"><span data-stu-id="90d58-121">Reference</span></span>  
 <span data-ttu-id="90d58-122"><xref:System.Windows.Forms.SplitContainer> 类</span><span class="sxs-lookup"><span data-stu-id="90d58-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="90d58-123">对此类进行描述，并提供指向其所有成员的链接。</span><span class="sxs-lookup"><span data-stu-id="90d58-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90d58-124">相关章节</span><span class="sxs-lookup"><span data-stu-id="90d58-124">Related Sections</span></span>  
 [<span data-ttu-id="90d58-125">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="90d58-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="90d58-126">提供指向有关专用于使用 Windows 窗体的控件的主题链接。</span><span class="sxs-lookup"><span data-stu-id="90d58-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="90d58-127">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="90d58-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="90d58-128">提供 Windows 窗体控件的完整列表，附带其使用情况相关信息的链接。</span><span class="sxs-lookup"><span data-stu-id="90d58-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
