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
# <a name="how-to-customize-the-ticks-on-a-slider"></a>如何：自定义滑块上的刻度
此示例演示如何创建<xref:System.Windows.Controls.Slider>带有刻度的控件。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.Primitives.TickBar>设置时将显示<xref:System.Windows.Controls.Slider.TickPlacement%2A>属性的值以外的其他<xref:System.Windows.Controls.Primitives.TickPlacement.None>，这是默认值。  
  
 下面的示例演示如何创建<xref:System.Windows.Controls.Slider>与<xref:System.Windows.Controls.Primitives.TickBar>显示刻度。 <xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>属性定义刻度线和它们之间的间隔的位置。 当您移动<xref:System.Windows.Controls.Primitives.Thumb>，工具提示显示的值<xref:System.Windows.Controls.Slider>。 <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>属性定义工具提示的出现。 <xref:System.Windows.Controls.Primitives.Thumb>移动对应于刻度线的位置，因为<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>设置为`true`。  
  
 下面的示例演示如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>属性来创建刻度线沿<xref:System.Windows.Controls.Slider>不规则间隔。  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [滑块操作说明主题](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
