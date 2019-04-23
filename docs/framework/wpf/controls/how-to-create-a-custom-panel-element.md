---
title: 如何：创建自定义 Panel 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: d4fc9d76ada9f27bd52619280b323691af9382c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139563"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="f50c2-102">如何：创建自定义 Panel 元素</span><span class="sxs-lookup"><span data-stu-id="f50c2-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="f50c2-103">示例</span><span class="sxs-lookup"><span data-stu-id="f50c2-103">Example</span></span>  
 <span data-ttu-id="f50c2-104">此示例演示如何重写的默认布局行为<xref:System.Windows.Controls.Panel>元素，并创建自定义布局元素派生自<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="f50c2-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="f50c2-105">该示例定义了一个简单的自定义<xref:System.Windows.Controls.Panel>元素称为`PlotPanel`，其中定位子元素根据两个硬编码 x 坐标和 y 坐标。</span><span class="sxs-lookup"><span data-stu-id="f50c2-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="f50c2-106">在此示例中，`x`并`y`都设置为`50`; 因此，所有子元素都放置在该位置上的 x 和 y 轴。</span><span class="sxs-lookup"><span data-stu-id="f50c2-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="f50c2-107">若要实现自定义<xref:System.Windows.Controls.Panel>行为，该示例使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f50c2-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="f50c2-108">每个方法返回<xref:System.Windows.Size>需要定位和呈现子元素的数据。</span><span class="sxs-lookup"><span data-stu-id="f50c2-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f50c2-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="f50c2-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="f50c2-110">面板概述</span><span class="sxs-lookup"><span data-stu-id="f50c2-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="f50c2-111">创建自定义内容换行面板示例</span><span class="sxs-lookup"><span data-stu-id="f50c2-111">Create a Custom Content-Wrapping Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159979)
