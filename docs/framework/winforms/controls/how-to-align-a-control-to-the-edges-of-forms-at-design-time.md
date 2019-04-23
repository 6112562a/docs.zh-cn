---
title: 如何：在设计时将控件与窗体边缘对齐
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 8ca6fd64edbd73301fd298f42c3d4d97d021888a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331854"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="5189e-102">如何：在设计时将控件与窗体边缘对齐</span><span class="sxs-lookup"><span data-stu-id="5189e-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="5189e-103">可以使控件与窗体的边缘对齐通过设置<xref:System.Windows.Forms.Control.Dock%2A>。</span><span class="sxs-lookup"><span data-stu-id="5189e-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="5189e-104">此属性指定控件在窗体中的驻留位置。</span><span class="sxs-lookup"><span data-stu-id="5189e-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="5189e-105">可以将 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为下列值：</span><span class="sxs-lookup"><span data-stu-id="5189e-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="5189e-106">设置</span><span class="sxs-lookup"><span data-stu-id="5189e-106">Setting</span></span>|<span data-ttu-id="5189e-107">控件上的效果</span><span class="sxs-lookup"><span data-stu-id="5189e-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="5189e-108">停靠到窗体底部。</span><span class="sxs-lookup"><span data-stu-id="5189e-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="5189e-109">占据窗体中的所有剩余空间。</span><span class="sxs-lookup"><span data-stu-id="5189e-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="5189e-110">停靠到窗体的左侧。</span><span class="sxs-lookup"><span data-stu-id="5189e-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="5189e-111">执行停靠任何位置，而是显示在指定的位置及其<xref:System.Windows.Forms.Control.Location%2A>。</span><span class="sxs-lookup"><span data-stu-id="5189e-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="5189e-112">停靠到窗体的右侧。</span><span class="sxs-lookup"><span data-stu-id="5189e-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="5189e-113">停靠到窗体的顶部。</span><span class="sxs-lookup"><span data-stu-id="5189e-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="5189e-114">此外可以在代码中设置这些值。</span><span class="sxs-lookup"><span data-stu-id="5189e-114">These values can also be set in code.</span></span> <span data-ttu-id="5189e-115">有关详细信息，请参阅[如何：将控件与窗体边缘对齐](how-to-align-a-control-to-the-edges-of-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="5189e-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5189e-116">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="5189e-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5189e-117">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="5189e-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5189e-118">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="5189e-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="5189e-119">若要在设计时设置控件的 Dock 属性</span><span class="sxs-lookup"><span data-stu-id="5189e-119">To set the Dock property for your control at design time</span></span>  
  
1. <span data-ttu-id="5189e-120">在 Windows 窗体设计器中，选择您的控件。</span><span class="sxs-lookup"><span data-stu-id="5189e-120">In the Windows Forms Designer, select your control.</span></span>  
  
2. <span data-ttu-id="5189e-121">在中**属性**窗口中，单击下拉列表框旁边的<xref:System.Windows.Forms.Control.Dock%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="5189e-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="5189e-122">表示六种可能的图形界面<xref:System.Windows.Forms.Control.Dock%2A>显示设置。</span><span class="sxs-lookup"><span data-stu-id="5189e-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3. <span data-ttu-id="5189e-123">选择合适的设置。</span><span class="sxs-lookup"><span data-stu-id="5189e-123">Choose the appropriate setting.</span></span>  
  
4. <span data-ttu-id="5189e-124">您的控件现在将停靠的设置指定的方式。</span><span class="sxs-lookup"><span data-stu-id="5189e-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5189e-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="5189e-125">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5189e-126">如何：将控件与窗体边缘对齐</span><span class="sxs-lookup"><span data-stu-id="5189e-126">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="5189e-127">演练：使用对齐线的 Windows 窗体上排列控件</span><span class="sxs-lookup"><span data-stu-id="5189e-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="5189e-128">如何：在 Windows 窗体上定位控件</span><span class="sxs-lookup"><span data-stu-id="5189e-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="5189e-129">如何：锚定和停靠在 TableLayoutPanel 控件中的子控件</span><span class="sxs-lookup"><span data-stu-id="5189e-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="5189e-130">如何：锚定和停靠子控件在 FlowLayoutPanel 控件中</span><span class="sxs-lookup"><span data-stu-id="5189e-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="5189e-131">演练：使用 TableLayoutPanel 的 Windows 窗体上排列控件</span><span class="sxs-lookup"><span data-stu-id="5189e-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="5189e-132">演练：使用 FlowLayoutPanel 的 Windows 窗体上排列控件</span><span class="sxs-lookup"><span data-stu-id="5189e-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="5189e-133">设计时开发 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="5189e-133">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
