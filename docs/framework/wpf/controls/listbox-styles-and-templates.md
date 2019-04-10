---
title: ListBox 样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: 441db59a6d04787985245db057074798bed6b3e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157048"
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="a1a30-102">ListBox 样式和模板</span><span class="sxs-lookup"><span data-stu-id="a1a30-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="a1a30-103">本主题介绍的样式和模板的<xref:System.Windows.Controls.ListBox>控件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a1a30-104">可以修改默认<xref:System.Windows.Controls.ControlTemplate>为控件提供唯一外观。</span><span class="sxs-lookup"><span data-stu-id="a1a30-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a1a30-105">有关详细信息，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a1a30-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="a1a30-106">ListBox 部件</span><span class="sxs-lookup"><span data-stu-id="a1a30-106">ListBox Parts</span></span>  
 <span data-ttu-id="a1a30-107"><xref:System.Windows.Controls.ListBox>控件没有任何命名的部件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="a1a30-108">当您创建<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.ListBox>，模板可能包含<xref:System.Windows.Controls.ItemsPresenter>内<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="a1a30-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="a1a30-109">(<xref:System.Windows.Controls.ItemsPresenter>显示在每个项<xref:System.Windows.Controls.ListBox>;<xref:System.Windows.Controls.ScrollViewer>控件内实现滚动)。</span><span class="sxs-lookup"><span data-stu-id="a1a30-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="a1a30-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子级<xref:System.Windows.Controls.ScrollViewer>，必须授予<xref:System.Windows.Controls.ItemsPresenter>名称， `ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="a1a30-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="a1a30-111">ListBox 状态</span><span class="sxs-lookup"><span data-stu-id="a1a30-111">ListBox States</span></span>  
 <span data-ttu-id="a1a30-112">下表列出了的可视状态<xref:System.Windows.Controls.ListBox>控件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="a1a30-113">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="a1a30-113">VisualState Name</span></span>|<span data-ttu-id="a1a30-114">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="a1a30-114">VisualStateGroup Name</span></span>|<span data-ttu-id="a1a30-115">描述</span><span class="sxs-lookup"><span data-stu-id="a1a30-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a1a30-116">有效</span><span class="sxs-lookup"><span data-stu-id="a1a30-116">Valid</span></span>|<span data-ttu-id="a1a30-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-117">ValidationStates</span></span>|<span data-ttu-id="a1a30-118">控件有效。</span><span class="sxs-lookup"><span data-stu-id="a1a30-118">The control is valid.</span></span>|  
|<span data-ttu-id="a1a30-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a1a30-119">InvalidFocused</span></span>|<span data-ttu-id="a1a30-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-120">ValidationStates</span></span>|<span data-ttu-id="a1a30-121">控件无效，但具有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="a1a30-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a1a30-122">InvalidUnfocused</span></span>|<span data-ttu-id="a1a30-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-123">ValidationStates</span></span>|<span data-ttu-id="a1a30-124">控件无效，并且没有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="a1a30-125">ListBoxItem 部件</span><span class="sxs-lookup"><span data-stu-id="a1a30-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="a1a30-126"><xref:System.Windows.Controls.ListBoxItem>控件没有任何命名的部件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="a1a30-127">ListBoxItem 状态</span><span class="sxs-lookup"><span data-stu-id="a1a30-127">ListBoxItem States</span></span>  
 <span data-ttu-id="a1a30-128">下表列出了的可视状态<xref:System.Windows.Controls.ListBox>控件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="a1a30-129">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="a1a30-129">VisualState Name</span></span>|<span data-ttu-id="a1a30-130">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="a1a30-130">VisualStateGroup Name</span></span>|<span data-ttu-id="a1a30-131">描述</span><span class="sxs-lookup"><span data-stu-id="a1a30-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a1a30-132">普通</span><span class="sxs-lookup"><span data-stu-id="a1a30-132">Normal</span></span>|<span data-ttu-id="a1a30-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-133">CommonStates</span></span>|<span data-ttu-id="a1a30-134">默认状态。</span><span class="sxs-lookup"><span data-stu-id="a1a30-134">The default state.</span></span>|  
|<span data-ttu-id="a1a30-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="a1a30-135">MouseOver</span></span>|<span data-ttu-id="a1a30-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-136">CommonStates</span></span>|<span data-ttu-id="a1a30-137">鼠标指针悬停在控件上。</span><span class="sxs-lookup"><span data-stu-id="a1a30-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="a1a30-138">已禁用</span><span class="sxs-lookup"><span data-stu-id="a1a30-138">Disabled</span></span>|<span data-ttu-id="a1a30-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-139">CommonStates</span></span>|<span data-ttu-id="a1a30-140">该项已禁用。</span><span class="sxs-lookup"><span data-stu-id="a1a30-140">The item is disabled.</span></span>|  
|<span data-ttu-id="a1a30-141">已设定焦点</span><span class="sxs-lookup"><span data-stu-id="a1a30-141">Focused</span></span>|<span data-ttu-id="a1a30-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-142">FocusStates</span></span>|<span data-ttu-id="a1a30-143">该项有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-143">The item has focus.</span></span>|  
|<span data-ttu-id="a1a30-144">失去焦点</span><span class="sxs-lookup"><span data-stu-id="a1a30-144">Unfocused</span></span>|<span data-ttu-id="a1a30-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-145">FocusStates</span></span>|<span data-ttu-id="a1a30-146">该项没有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="a1a30-147">未选定</span><span class="sxs-lookup"><span data-stu-id="a1a30-147">Unselected</span></span>|<span data-ttu-id="a1a30-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-148">SelectionStates</span></span>|<span data-ttu-id="a1a30-149">未选定该项。</span><span class="sxs-lookup"><span data-stu-id="a1a30-149">The item is not selected.</span></span>|  
|<span data-ttu-id="a1a30-150">已选定</span><span class="sxs-lookup"><span data-stu-id="a1a30-150">Selected</span></span>|<span data-ttu-id="a1a30-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-151">SelectionStates</span></span>|<span data-ttu-id="a1a30-152">该项当前已选定。</span><span class="sxs-lookup"><span data-stu-id="a1a30-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="a1a30-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="a1a30-153">SelectedUnfocused</span></span>|<span data-ttu-id="a1a30-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-154">SelectionStates</span></span>|<span data-ttu-id="a1a30-155">该项已选定，但没有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="a1a30-156">有效</span><span class="sxs-lookup"><span data-stu-id="a1a30-156">Valid</span></span>|<span data-ttu-id="a1a30-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-157">ValidationStates</span></span>|<span data-ttu-id="a1a30-158">该控件使用<xref:System.Windows.Controls.Validation>类和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`false`。</span><span class="sxs-lookup"><span data-stu-id="a1a30-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a1a30-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a1a30-159">InvalidFocused</span></span>|<span data-ttu-id="a1a30-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-160">ValidationStates</span></span>|<span data-ttu-id="a1a30-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`已在控件有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a1a30-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a1a30-162">InvalidUnfocused</span></span>|<span data-ttu-id="a1a30-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a1a30-163">ValidationStates</span></span>|<span data-ttu-id="a1a30-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`具有该控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="a1a30-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="a1a30-165">ListBox ControlTemplate 示例</span><span class="sxs-lookup"><span data-stu-id="a1a30-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="a1a30-166">下面的示例演示如何定义<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.ListBoxItem>控件。</span><span class="sxs-lookup"><span data-stu-id="a1a30-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="a1a30-167">上一示例使用了一个或多个以下资源。</span><span class="sxs-lookup"><span data-stu-id="a1a30-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a1a30-168">有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="a1a30-168">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a30-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1a30-169">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="a1a30-170">Control 样式和模板</span><span class="sxs-lookup"><span data-stu-id="a1a30-170">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="a1a30-171">控件自定义</span><span class="sxs-lookup"><span data-stu-id="a1a30-171">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="a1a30-172">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="a1a30-172">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="a1a30-173">通过创建 ControlTemplate 自定义现有控件的外观</span><span class="sxs-lookup"><span data-stu-id="a1a30-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
