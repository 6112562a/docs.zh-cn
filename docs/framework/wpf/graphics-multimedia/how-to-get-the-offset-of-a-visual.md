---
title: 如何：获取 Visual 的偏移量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: ea03f7b9c3fefde0efa3fa0daaa07a537618f37a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374318"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="6f131-102">如何：获取 Visual 的偏移量</span><span class="sxs-lookup"><span data-stu-id="6f131-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="6f131-103">这些示例显示如何检索相对于其父级或任何祖先或后代的可视对象的偏移量的值。</span><span class="sxs-lookup"><span data-stu-id="6f131-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f131-104">示例</span><span class="sxs-lookup"><span data-stu-id="6f131-104">Example</span></span>  
 <span data-ttu-id="6f131-105">以下标记示例演示<xref:System.Windows.Controls.TextBlock>定义与<xref:System.Windows.FrameworkElement.Margin%2A>值为 4。</span><span class="sxs-lookup"><span data-stu-id="6f131-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="6f131-106">下面的代码示例演示如何使用<xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="6f131-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="6f131-107">偏移量的值包含在返回<xref:System.Windows.Vector>值。</span><span class="sxs-lookup"><span data-stu-id="6f131-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="6f131-108">偏移量将考虑<xref:System.Windows.FrameworkElement.Margin%2A>值。</span><span class="sxs-lookup"><span data-stu-id="6f131-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="6f131-109">在这种情况下，<xref:System.Windows.Vector.X%2A>为 4，和<xref:System.Windows.Vector.Y%2A>为 4。</span><span class="sxs-lookup"><span data-stu-id="6f131-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="6f131-110">返回的偏移量的值是相对于父级的<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="6f131-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="6f131-111">如果你想要返回的不是相对于父级的偏移量的值<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6f131-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="6f131-112">获取偏移量相对于上级</span><span class="sxs-lookup"><span data-stu-id="6f131-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="6f131-113">以下标记示例演示<xref:System.Windows.Controls.TextBlock>嵌套在两个<xref:System.Windows.Controls.StackPanel>对象。</span><span class="sxs-lookup"><span data-stu-id="6f131-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="6f131-114">下图显示标记的结果。</span><span class="sxs-lookup"><span data-stu-id="6f131-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="6f131-115">![对象的偏移量值](./media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="6f131-115">![Offset values of objects](./media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="6f131-116">嵌套在两个面板的 TextBlock</span><span class="sxs-lookup"><span data-stu-id="6f131-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="6f131-117">下面的代码示例演示如何使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.TextBlock>相对于包含<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="6f131-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6f131-118">偏移量的值包含在返回<xref:System.Windows.Media.GeneralTransform>值。</span><span class="sxs-lookup"><span data-stu-id="6f131-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="6f131-119">偏移量会考虑<xref:System.Windows.FrameworkElement.Margin%2A>值中包含的所有对象<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="6f131-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6f131-120">在这种情况下，<xref:System.Windows.Vector.X%2A>为 28 (16 + 8 + 4) 和<xref:System.Windows.Vector.Y%2A>为 28。</span><span class="sxs-lookup"><span data-stu-id="6f131-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="6f131-121">返回的偏移量的值是相对于相对的祖先<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="6f131-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="6f131-122">如果你想要返回的偏移量的值是相对于的后代<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6f131-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="6f131-123">获取偏移量相对于后代</span><span class="sxs-lookup"><span data-stu-id="6f131-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="6f131-124">以下标记示例演示<xref:System.Windows.Controls.TextBlock>包含在<xref:System.Windows.Controls.StackPanel>对象。</span><span class="sxs-lookup"><span data-stu-id="6f131-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="6f131-125">下面的代码示例演示如何使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.StackPanel>相对于其子<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="6f131-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="6f131-126">偏移量的值包含在返回<xref:System.Windows.Media.GeneralTransform>值。</span><span class="sxs-lookup"><span data-stu-id="6f131-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="6f131-127">偏移量将考虑<xref:System.Windows.FrameworkElement.Margin%2A>的所有对象的值。</span><span class="sxs-lookup"><span data-stu-id="6f131-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="6f131-128">在这种情况下，<xref:System.Windows.Vector.X%2A>为-4，和<xref:System.Windows.Vector.Y%2A>-4。</span><span class="sxs-lookup"><span data-stu-id="6f131-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="6f131-129">偏移量的值是负值，因为父对象产生负面偏移量相对于其子对象。</span><span class="sxs-lookup"><span data-stu-id="6f131-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f131-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f131-130">See also</span></span>
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="6f131-131">WPF 图形呈现概述</span><span class="sxs-lookup"><span data-stu-id="6f131-131">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
