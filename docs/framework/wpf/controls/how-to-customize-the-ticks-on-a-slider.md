---
title: 如何：自定义滑块上的刻度
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: b6ade07b0b4c04578d2523d6d8ba992b8b2d31f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696667"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="ce715-102">如何：自定义滑块上的刻度</span><span class="sxs-lookup"><span data-stu-id="ce715-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="ce715-103">此示例演示如何创建<xref:System.Windows.Controls.Slider>带有刻度的控件。</span><span class="sxs-lookup"><span data-stu-id="ce715-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce715-104">示例</span><span class="sxs-lookup"><span data-stu-id="ce715-104">Example</span></span>  
 <span data-ttu-id="ce715-105"><xref:System.Windows.Controls.Primitives.TickBar>设置时将显示<xref:System.Windows.Controls.Slider.TickPlacement%2A>属性的值以外的其他<xref:System.Windows.Controls.Primitives.TickPlacement.None>，这是默认值。</span><span class="sxs-lookup"><span data-stu-id="ce715-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="ce715-106">下面的示例演示如何创建<xref:System.Windows.Controls.Slider>与<xref:System.Windows.Controls.Primitives.TickBar>显示刻度。</span><span class="sxs-lookup"><span data-stu-id="ce715-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="ce715-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>属性定义刻度线和它们之间的间隔的位置。</span><span class="sxs-lookup"><span data-stu-id="ce715-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="ce715-108">当您移动<xref:System.Windows.Controls.Primitives.Thumb>，工具提示显示的值<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="ce715-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="ce715-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>属性定义工具提示的出现。</span><span class="sxs-lookup"><span data-stu-id="ce715-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="ce715-110"><xref:System.Windows.Controls.Primitives.Thumb>移动对应于刻度线的位置，因为<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="ce715-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="ce715-111">下面的示例演示如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>属性来创建刻度线沿<xref:System.Windows.Controls.Slider>不规则间隔。</span><span class="sxs-lookup"><span data-stu-id="ce715-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ce715-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce715-112">See also</span></span>
- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [<span data-ttu-id="ce715-113">滑块操作说明主题</span><span class="sxs-lookup"><span data-stu-id="ce715-113">Slider How-to Topics</span></span>](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
