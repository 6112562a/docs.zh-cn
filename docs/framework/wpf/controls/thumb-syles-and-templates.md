---
title: Thumb 样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: e987932e00be09fdf5ac34bb2bfb24a890368a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596379"
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="eace0-102">Thumb 样式和模板</span><span class="sxs-lookup"><span data-stu-id="eace0-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="eace0-103">本主题介绍的样式和模板的<xref:System.Windows.Controls.Primitives.Thumb>控件。</span><span class="sxs-lookup"><span data-stu-id="eace0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="eace0-104">可以修改默认<xref:System.Windows.Controls.ControlTemplate>为控件提供唯一外观。</span><span class="sxs-lookup"><span data-stu-id="eace0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="eace0-105">有关详细信息，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="eace0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="eace0-106">Thumb 部件</span><span class="sxs-lookup"><span data-stu-id="eace0-106">Thumb Parts</span></span>  
 <span data-ttu-id="eace0-107"><xref:System.Windows.Controls.Primitives.Thumb>控件没有任何命名的部件。</span><span class="sxs-lookup"><span data-stu-id="eace0-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="eace0-108">Thumb 状态</span><span class="sxs-lookup"><span data-stu-id="eace0-108">Thumb States</span></span>  
 <span data-ttu-id="eace0-109">下表列出了的可视状态<xref:System.Windows.Controls.Primitives.Thumb>控件。</span><span class="sxs-lookup"><span data-stu-id="eace0-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="eace0-110">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="eace0-110">VisualState Name</span></span>|<span data-ttu-id="eace0-111">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="eace0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="eace0-112">描述</span><span class="sxs-lookup"><span data-stu-id="eace0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="eace0-113">普通</span><span class="sxs-lookup"><span data-stu-id="eace0-113">Normal</span></span>|<span data-ttu-id="eace0-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eace0-114">CommonStates</span></span>|<span data-ttu-id="eace0-115">默认状态。</span><span class="sxs-lookup"><span data-stu-id="eace0-115">The default state.</span></span>|  
|<span data-ttu-id="eace0-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="eace0-116">MouseOver</span></span>|<span data-ttu-id="eace0-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eace0-117">CommonStates</span></span>|<span data-ttu-id="eace0-118">鼠标指针悬停在控件上方。</span><span class="sxs-lookup"><span data-stu-id="eace0-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="eace0-119">已按下</span><span class="sxs-lookup"><span data-stu-id="eace0-119">Pressed</span></span>|<span data-ttu-id="eace0-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eace0-120">CommonStates</span></span>|<span data-ttu-id="eace0-121">已按下控件。</span><span class="sxs-lookup"><span data-stu-id="eace0-121">The control is pressed.</span></span>|  
|<span data-ttu-id="eace0-122">已禁用</span><span class="sxs-lookup"><span data-stu-id="eace0-122">Disabled</span></span>|<span data-ttu-id="eace0-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eace0-123">CommonStates</span></span>|<span data-ttu-id="eace0-124">已禁用控件。</span><span class="sxs-lookup"><span data-stu-id="eace0-124">The control is disabled.</span></span>|  
|<span data-ttu-id="eace0-125">已设定焦点</span><span class="sxs-lookup"><span data-stu-id="eace0-125">Focused</span></span>|<span data-ttu-id="eace0-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eace0-126">FocusStates</span></span>|<span data-ttu-id="eace0-127">控件有焦点。</span><span class="sxs-lookup"><span data-stu-id="eace0-127">The control has focus.</span></span>|  
|<span data-ttu-id="eace0-128">失去焦点</span><span class="sxs-lookup"><span data-stu-id="eace0-128">Unfocused</span></span>|<span data-ttu-id="eace0-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eace0-129">FocusStates</span></span>|<span data-ttu-id="eace0-130">控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="eace0-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="eace0-131">有效</span><span class="sxs-lookup"><span data-stu-id="eace0-131">Valid</span></span>|<span data-ttu-id="eace0-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eace0-132">ValidationStates</span></span>|<span data-ttu-id="eace0-133">该控件使用<xref:System.Windows.Controls.Validation>类和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`false`。</span><span class="sxs-lookup"><span data-stu-id="eace0-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="eace0-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="eace0-134">InvalidFocused</span></span>|<span data-ttu-id="eace0-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eace0-135">ValidationStates</span></span>|<span data-ttu-id="eace0-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`已在控件有焦点。</span><span class="sxs-lookup"><span data-stu-id="eace0-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="eace0-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="eace0-137">InvalidUnfocused</span></span>|<span data-ttu-id="eace0-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eace0-138">ValidationStates</span></span>|<span data-ttu-id="eace0-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`具有该控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="eace0-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="eace0-140">Thumb 的 ControlTemplate 示例</span><span class="sxs-lookup"><span data-stu-id="eace0-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="eace0-141">下面的示例演示如何定义<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Primitives.Thumb>控件。</span><span class="sxs-lookup"><span data-stu-id="eace0-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="eace0-142">上一示例使用了一个或多个以下资源。</span><span class="sxs-lookup"><span data-stu-id="eace0-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="eace0-143">有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="eace0-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eace0-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="eace0-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="eace0-145">控件样式和模板</span><span class="sxs-lookup"><span data-stu-id="eace0-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="eace0-146">控件自定义</span><span class="sxs-lookup"><span data-stu-id="eace0-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="eace0-147">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="eace0-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="eace0-148">通过创建 ControlTemplate 自定义现有控件的外观</span><span class="sxs-lookup"><span data-stu-id="eace0-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
