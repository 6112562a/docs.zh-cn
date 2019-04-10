---
title: 如何：设置 Windows 窗体上的 Tab 键顺序
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 50f5f91a946aeebc4d82630b25d18d8f8d2ea4be
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339900"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a><span data-ttu-id="994b3-102">如何：设置 Windows 窗体上的 Tab 键顺序</span><span class="sxs-lookup"><span data-stu-id="994b3-102">How to: Set the Tab Order on Windows Forms</span></span>
<span data-ttu-id="994b3-103">Tab 键顺序是在其中用户焦点从一个控件移到另一个通过按 TAB 键顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-103">The tab order is the order in which a user moves focus from one control to another by pressing the TAB key.</span></span> <span data-ttu-id="994b3-104">每个窗体具有其自己的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-104">Each form has its own tab order.</span></span> <span data-ttu-id="994b3-105">默认情况下，tab 键顺序是在其中创建控件的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="994b3-105">By default, the tab order is the same as the order in which you created the controls.</span></span> <span data-ttu-id="994b3-106">Tab 键顺序编号从 0 开始。</span><span class="sxs-lookup"><span data-stu-id="994b3-106">Tab-order numbering begins with zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="994b3-107">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="994b3-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="994b3-108">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="994b3-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="994b3-109">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="994b3-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-tab-order-of-a-control"></a><span data-ttu-id="994b3-110">若要设置控件的 tab 键顺序</span><span class="sxs-lookup"><span data-stu-id="994b3-110">To set the tab order of a control</span></span>  
  
1. <span data-ttu-id="994b3-111">上**视图**菜单上，单击**tab 键顺序**。</span><span class="sxs-lookup"><span data-stu-id="994b3-111">On the **View** menu, click **Tab Order**.</span></span>  
  
     <span data-ttu-id="994b3-112">这将激活窗体上的 tab 键顺序选择模式。</span><span class="sxs-lookup"><span data-stu-id="994b3-112">This activates the tab-order selection mode on the form.</span></span> <span data-ttu-id="994b3-113">一个数字 (表示<xref:System.Windows.Forms.Control.TabIndex%2A>属性) 中的每个控件的左上角显示。</span><span class="sxs-lookup"><span data-stu-id="994b3-113">A number (representing the <xref:System.Windows.Forms.Control.TabIndex%2A> property) appears in the upper-left corner of each control.</span></span>  
  
2. <span data-ttu-id="994b3-114">单击控件以建立所需的选项卡顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-114">Click the controls sequentially to establish the tab order you want.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="994b3-115">大于或等于 0，可以为任何值设置 tab 键顺序中的控件的位置。</span><span class="sxs-lookup"><span data-stu-id="994b3-115">A control's place within the tab order can be set to any value greater than or equal to 0.</span></span> <span data-ttu-id="994b3-116">重复发生时，计算两个控件的 z 顺序，并为第一个选项卡顶部的控件。</span><span class="sxs-lookup"><span data-stu-id="994b3-116">When duplicates occur, the z-order of the two controls is evaluated and the control on top is tabbed to first.</span></span> <span data-ttu-id="994b3-117">（z 顺序是沿窗体的 z 轴 [深度] 窗体上控件的可视化分层。</span><span class="sxs-lookup"><span data-stu-id="994b3-117">(The z-order is the visual layering of controls on a form along the form's z-axis [depth].</span></span> <span data-ttu-id="994b3-118">Z 顺序确定哪些控件位于其他控件的前面。）Z 顺序的详细信息，请参阅[在 Windows 窗体上的分层对象](how-to-layer-objects-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="994b3-118">The z-order determines which controls are in front of other controls.) For more information on z-order, see [Layering Objects on Windows Forms](how-to-layer-objects-on-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="994b3-119">完成后，单击**tab 键顺序**上**视图**菜单，再次将 tab 键顺序模式。</span><span class="sxs-lookup"><span data-stu-id="994b3-119">When you have finished, click **Tab Order** on the **View** menu again to leave tab order mode.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="994b3-120">无法获取焦点的控件，以及已禁用且不可见控件不具有<xref:System.Windows.Forms.Control.TabIndex%2A>属性并且将不包含在 tab 键顺序中。</span><span class="sxs-lookup"><span data-stu-id="994b3-120">Controls that cannot get the focus, as well as disabled and invisible controls, do not have a <xref:System.Windows.Forms.Control.TabIndex%2A> property and are not included in the tab order.</span></span> <span data-ttu-id="994b3-121">当用户按 TAB 键，将跳过这些控件。</span><span class="sxs-lookup"><span data-stu-id="994b3-121">As a user presses the TAB key, these controls are skipped.</span></span>  
  
 <span data-ttu-id="994b3-122">或者，可以在属性窗口中使用设置 tab 键顺序<xref:System.Windows.Forms.Control.TabIndex%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="994b3-122">Alternatively, tab order can be set in the Properties window using the <xref:System.Windows.Forms.Control.TabIndex%2A> property.</span></span> <span data-ttu-id="994b3-123"><xref:System.Windows.Forms.Control.TabIndex%2A>控件的属性确定其定位的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-123">The <xref:System.Windows.Forms.Control.TabIndex%2A> property of a control determines where it is positioned in the tab order.</span></span> <span data-ttu-id="994b3-124">默认情况下，具有第一个控件绘制<xref:System.Windows.Forms.Control.TabIndex%2A>值为 0，第二个<xref:System.Windows.Forms.Control.TabIndex%2A>为 1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="994b3-124">By default, the first control drawn has a <xref:System.Windows.Forms.Control.TabIndex%2A> value of 0, the second has a <xref:System.Windows.Forms.Control.TabIndex%2A> of 1, and so on.</span></span>  
  
 <span data-ttu-id="994b3-125">此外，默认情况下，<xref:System.Windows.Forms.GroupBox>控件具有其自己<xref:System.Windows.Forms.Control.TabIndex%2A>值，该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="994b3-125">Additionally, by default, a <xref:System.Windows.Forms.GroupBox> control has its own <xref:System.Windows.Forms.Control.TabIndex%2A> value, which is a whole number.</span></span> <span data-ttu-id="994b3-126">一个<xref:System.Windows.Forms.GroupBox>控件本身不能在运行时具有焦点。</span><span class="sxs-lookup"><span data-stu-id="994b3-126">A <xref:System.Windows.Forms.GroupBox> control itself cannot have focus at run time.</span></span> <span data-ttu-id="994b3-127">因此，在每个控件<xref:System.Windows.Forms.GroupBox>具有其自己的十进制<xref:System.Windows.Forms.Control.TabIndex%2A>值，从.0 开始。</span><span class="sxs-lookup"><span data-stu-id="994b3-127">Thus, each control within a <xref:System.Windows.Forms.GroupBox> has its own decimal <xref:System.Windows.Forms.Control.TabIndex%2A> value, beginning with .0.</span></span> <span data-ttu-id="994b3-128">当然，作为<xref:System.Windows.Forms.Control.TabIndex%2A>的<xref:System.Windows.Forms.GroupBox>递增控件时，将相应递增中它的控件。</span><span class="sxs-lookup"><span data-stu-id="994b3-128">Naturally, as the <xref:System.Windows.Forms.Control.TabIndex%2A> of a <xref:System.Windows.Forms.GroupBox> control is incremented, the controls within it will be incremented accordingly.</span></span> <span data-ttu-id="994b3-129">如果您更改<xref:System.Windows.Forms.Control.TabIndex%2A>介于 5 和 6，<xref:System.Windows.Forms.Control.TabIndex%2A>其组中的第一个控件的值将自动更改为 6.0 中，依次类推。</span><span class="sxs-lookup"><span data-stu-id="994b3-129">If you changed a <xref:System.Windows.Forms.Control.TabIndex%2A> value from 5 to 6, the <xref:System.Windows.Forms.Control.TabIndex%2A> value of the first control in its group automatically changes to 6.0, and so on.</span></span>  
  
 <span data-ttu-id="994b3-130">最后，任何窗体上的多个控件可以跳过的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-130">Finally, any control of the many on your form can be skipped in the tab order.</span></span> <span data-ttu-id="994b3-131">通常情况下，连续按 tab 键在运行的时选择每个控件的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="994b3-131">Usually, pressing TAB successively at run time selects each control in the tab order.</span></span> <span data-ttu-id="994b3-132">通过关闭<xref:System.Windows.Forms.Control.TabStop%2A>属性，可以使窗体的 tab 键顺序通过传递控件。</span><span class="sxs-lookup"><span data-stu-id="994b3-132">By turning off the <xref:System.Windows.Forms.Control.TabStop%2A> property, you can make a control be passed over in the tab order of the form.</span></span>  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a><span data-ttu-id="994b3-133">若要从 tab 键顺序中移除控件</span><span class="sxs-lookup"><span data-stu-id="994b3-133">To remove a control from the tab order</span></span>  
  
1. <span data-ttu-id="994b3-134">设置控件的<xref:System.Windows.Forms.Control.TabStop%2A>属性设置为`false`属性窗口中。</span><span class="sxs-lookup"><span data-stu-id="994b3-134">Set the control's <xref:System.Windows.Forms.Control.TabStop%2A> property to `false` in the Properties window.</span></span>  
  
     <span data-ttu-id="994b3-135">一个控件<xref:System.Windows.Forms.Control.TabStop%2A>属性已设置为`false`仍保持其 tab 键顺序中的位置，即使控件循环使用 TAB 键时，将跳过该控件。</span><span class="sxs-lookup"><span data-stu-id="994b3-135">A control whose <xref:System.Windows.Forms.Control.TabStop%2A> property has been set to `false` still maintains its position in the tab order, even though the control is skipped when you cycle through the controls with the TAB key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="994b3-136">单选按钮组具有一个选项卡在运行时停止。</span><span class="sxs-lookup"><span data-stu-id="994b3-136">A radio button group has a single tab stop at run time.</span></span> <span data-ttu-id="994b3-137">选定的按钮 (即，具有按钮及其<xref:System.Windows.Forms.RadioButton.Checked%2A>属性设置为`true`) 具有其<xref:System.Windows.Forms.Control.TabStop%2A>属性自动设置为`true`，而其他按钮都有其<xref:System.Windows.Forms.Control.TabStop%2A>属性设置为`false`。</span><span class="sxs-lookup"><span data-stu-id="994b3-137">The selected button (that is, the button with its <xref:System.Windows.Forms.RadioButton.Checked%2A> property set to `true`) has its <xref:System.Windows.Forms.Control.TabStop%2A> property automatically set to `true`, while the other buttons have their <xref:System.Windows.Forms.Control.TabStop%2A> property set to `false`.</span></span> <span data-ttu-id="994b3-138">有关分组的详细信息<xref:System.Windows.Forms.RadioButton>控件，请参阅[分组 Windows 窗体 RadioButton 控件按功能](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。</span><span class="sxs-lookup"><span data-stu-id="994b3-138">For more information about grouping <xref:System.Windows.Forms.RadioButton> controls, see [Grouping Windows Forms RadioButton Controls to Function as a Set](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994b3-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="994b3-139">See also</span></span>

- [<span data-ttu-id="994b3-140">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="994b3-140">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="994b3-141">排列 Windows 窗体上的控件</span><span class="sxs-lookup"><span data-stu-id="994b3-141">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="994b3-142">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="994b3-142">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="994b3-143">根据功能列出的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="994b3-143">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
