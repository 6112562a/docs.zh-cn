---
title: TabControl 控件（Windows 窗体）
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
ms.openlocfilehash: d00dbe1e450a2d4316709e92eff7dab488b36045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755371"
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="c02b9-102">TabControl 控件（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="c02b9-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="c02b9-103">Windows 窗体 `TabControl` 显示多个选项卡，就像笔记本中的分隔线或档案柜中一组文件夹的标签。</span><span class="sxs-lookup"><span data-stu-id="c02b9-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="c02b9-104">选项卡可以包含图片和其他控件。</span><span class="sxs-lookup"><span data-stu-id="c02b9-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="c02b9-105">使用 `TabControl` 创建属性页。</span><span class="sxs-lookup"><span data-stu-id="c02b9-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c02b9-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="c02b9-106">In This Section</span></span>  
 [<span data-ttu-id="c02b9-107">TabControl 控件概述</span><span class="sxs-lookup"><span data-stu-id="c02b9-107">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="c02b9-108">说明此控件的本质及其主要功能和属性。</span><span class="sxs-lookup"><span data-stu-id="c02b9-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="c02b9-109">如何：向选项卡页添加控件</span><span class="sxs-lookup"><span data-stu-id="c02b9-109">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="c02b9-110">提供有关在选项卡页上显示控件的指导。</span><span class="sxs-lookup"><span data-stu-id="c02b9-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="c02b9-111">如何：添加和删除使用 Windows 窗体 TabControl 的选项卡</span><span class="sxs-lookup"><span data-stu-id="c02b9-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="c02b9-112">提供有关在设计器或代码中添加和移除选项卡的指导。</span><span class="sxs-lookup"><span data-stu-id="c02b9-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="c02b9-113">如何：更改 Windows 窗体 TabControl 的外观</span><span class="sxs-lookup"><span data-stu-id="c02b9-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="c02b9-114">提供有关调整影响单个选项卡外观的属性的指导。</span><span class="sxs-lookup"><span data-stu-id="c02b9-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="c02b9-115">如何：禁用选项卡页</span><span class="sxs-lookup"><span data-stu-id="c02b9-115">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)  
 <span data-ttu-id="c02b9-116">说明如何限制对选项卡页的访问，可能根据用户凭据进行限制。</span><span class="sxs-lookup"><span data-stu-id="c02b9-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="c02b9-117">另请参阅[如何：添加和删除使用 Windows 窗体 tabcontrol 控件使用设计器选项卡](add-and-remove-tabs-with-wf-tabcontrol-using-the-designer.md)，[如何：向使用设计器的选项卡页添加控件](how-to-add-a-control-to-a-tab-page-using-the-designer.md)</span><span class="sxs-lookup"><span data-stu-id="c02b9-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](add-and-remove-tabs-with-wf-tabcontrol-using-the-designer.md), [How to: Add a Control to a Tab Page Using the Designer](how-to-add-a-control-to-a-tab-page-using-the-designer.md)</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c02b9-118">参考</span><span class="sxs-lookup"><span data-stu-id="c02b9-118">Reference</span></span>  
 <span data-ttu-id="c02b9-119"><xref:System.Windows.Forms.TabControl> 类</span><span class="sxs-lookup"><span data-stu-id="c02b9-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="c02b9-120">对此类进行描述，并提供指向其所有成员的链接。</span><span class="sxs-lookup"><span data-stu-id="c02b9-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c02b9-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="c02b9-121">Related Sections</span></span>  
 [<span data-ttu-id="c02b9-122">Windows 窗体中的对话框</span><span class="sxs-lookup"><span data-stu-id="c02b9-122">Dialog Boxes in Windows Forms</span></span>](../dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="c02b9-123">提供对话框的任务列表，它通常显示选项卡。</span><span class="sxs-lookup"><span data-stu-id="c02b9-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="c02b9-124">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="c02b9-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="c02b9-125">提供 Windows 窗体控件的完整列表，附带其使用情况相关信息的链接。</span><span class="sxs-lookup"><span data-stu-id="c02b9-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
