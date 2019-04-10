---
title: 如何：绘制线条
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: c11dfb9523834ec2e622cb2e62bd6982a1a78fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143515"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="b3db1-102">如何：绘制线条</span><span class="sxs-lookup"><span data-stu-id="b3db1-102">How to: Draw a Line</span></span>
<span data-ttu-id="b3db1-103">此示例演示如何通过使用绘制线条<xref:System.Windows.Shapes.Line>元素。</span><span class="sxs-lookup"><span data-stu-id="b3db1-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="b3db1-104">若要绘制一条线，请创建<xref:System.Windows.Shapes.Line>元素。</span><span class="sxs-lookup"><span data-stu-id="b3db1-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="b3db1-105">使用其<xref:System.Windows.Shapes.Line.X1%2A>并<xref:System.Windows.Shapes.Line.Y1%2A>属性来设置其开始点; 并使用其<xref:System.Windows.Shapes.Line.X2%2A>和<xref:System.Windows.Shapes.Line.Y2%2A>要设置其终结点的属性。</span><span class="sxs-lookup"><span data-stu-id="b3db1-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="b3db1-106">最后，设置其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>因为没有笔画行是不可见。</span><span class="sxs-lookup"><span data-stu-id="b3db1-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="b3db1-107">设置<xref:System.Windows.Shapes.Shape.Fill%2A>行的元素具有不起作用，由于直线没有内部区域。</span><span class="sxs-lookup"><span data-stu-id="b3db1-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="b3db1-108">下面的示例绘制内的三个行<xref:System.Windows.Controls.Canvas>元素。</span><span class="sxs-lookup"><span data-stu-id="b3db1-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3db1-109">示例</span><span class="sxs-lookup"><span data-stu-id="b3db1-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="b3db1-110">此示例摘自一个更大的示例;有关完整示例，请参阅[形状元素示例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="b3db1-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3db1-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="b3db1-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="b3db1-112">形状元素示例</span><span class="sxs-lookup"><span data-stu-id="b3db1-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
