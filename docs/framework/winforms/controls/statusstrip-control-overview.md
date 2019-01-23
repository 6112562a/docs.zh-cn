---
title: StatusStrip 控件概述
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: 9356ca85003987eabf4f62a25acad45d73e144fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627234"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="15139-102">StatusStrip 控件概述</span><span class="sxs-lookup"><span data-stu-id="15139-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="15139-103"><xref:System.Windows.Forms.StatusStrip> 控件将显示有关在 <xref:System.Windows.Forms.Form> 上查看的对象、对象组件的信息或应用程序内与该对象操作相关的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="15139-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="15139-104">通常，<xref:System.Windows.Forms.StatusStrip> 控件由 <xref:System.Windows.Forms.ToolStripStatusLabel> 对象组成，每个对象将显示文本、图标或两者都有。</span><span class="sxs-lookup"><span data-stu-id="15139-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="15139-105"><xref:System.Windows.Forms.StatusStrip> 也可以包括 <xref:System.Windows.Forms.ToolStripDropDownButton>、<xref:System.Windows.Forms.ToolStripSplitButton> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 控件。</span><span class="sxs-lookup"><span data-stu-id="15139-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="15139-106">默认 <xref:System.Windows.Forms.StatusStrip> 没有面板。</span><span class="sxs-lookup"><span data-stu-id="15139-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="15139-107">若要将面板添加到 <xref:System.Windows.Forms.StatusStrip>，则使用 <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="15139-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="15139-108">广泛支持用于处理 <xref:System.Windows.Forms.StatusStrip> 项目和 Visual Studio 中的常见命令。</span><span class="sxs-lookup"><span data-stu-id="15139-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="15139-109">另请参阅[StatusStrip 项集合编辑器](https://msdn.microsoft.com/library/ms233631\(v=vs.110\))， [StatusStrip 任务对话框](https://msdn.microsoft.com/library/ms233642\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="15139-109">Also see [StatusStrip Items Collection Editor](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="15139-110">尽管 <xref:System.Windows.Forms.StatusStrip> 替换并扩展了早期版本的 <xref:System.Windows.Forms.StatusBar> 控件，但也可以选择保留 <xref:System.Windows.Forms.StatusBar> 以备向后兼容性和将来使用。</span><span class="sxs-lookup"><span data-stu-id="15139-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="15139-111">重要 StatusStrip 成员</span><span class="sxs-lookup"><span data-stu-id="15139-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="15139-112">名称</span><span class="sxs-lookup"><span data-stu-id="15139-112">Name</span></span>|<span data-ttu-id="15139-113">描述</span><span class="sxs-lookup"><span data-stu-id="15139-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="15139-114">获取或设置一个值，该值指示 <xref:System.Windows.Forms.StatusStrip> 是否支持溢出功能。</span><span class="sxs-lookup"><span data-stu-id="15139-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="15139-115">获取或设置一个值，该值指示 <xref:System.Windows.Forms.StatusStrip> 是否在其 <xref:System.Windows.Forms.ToolStripContainer> 中从一端拉伸到了另一端。</span><span class="sxs-lookup"><span data-stu-id="15139-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="15139-116">重要 StatusStrip 伴随类</span><span class="sxs-lookup"><span data-stu-id="15139-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="15139-117">名称</span><span class="sxs-lookup"><span data-stu-id="15139-117">Name</span></span>|<span data-ttu-id="15139-118">描述</span><span class="sxs-lookup"><span data-stu-id="15139-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="15139-119">表示 <xref:System.Windows.Forms.StatusStrip> 控件中的一个面板。</span><span class="sxs-lookup"><span data-stu-id="15139-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="15139-120">显示一个相关联的 <xref:System.Windows.Forms.ToolStripDropDown>，用户可以从中选择单个项目。</span><span class="sxs-lookup"><span data-stu-id="15139-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="15139-121">表示一个两部分的控件，其中包括一个标准按钮和一个下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="15139-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="15139-122">显示进程的完成状态。</span><span class="sxs-lookup"><span data-stu-id="15139-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15139-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="15139-123">See also</span></span>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
