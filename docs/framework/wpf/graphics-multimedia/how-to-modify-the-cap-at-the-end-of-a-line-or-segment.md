---
title: 如何：修改直线或线段末端的线帽
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916139"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="23c6b-102">如何：修改直线或线段末端的线帽</span><span class="sxs-lookup"><span data-stu-id="23c6b-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="23c6b-103">此示例演示如何修改 open <xref:System.Windows.Shapes.Shape>元素开头或结尾处的形状。</span><span class="sxs-lookup"><span data-stu-id="23c6b-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="23c6b-104">若要更改打开<xref:System.Windows.Shapes.Shape>的开头的端点, 请使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="23c6b-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="23c6b-105">若要更改打开<xref:System.Windows.Shapes.Shape>的末尾的端点, 请使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="23c6b-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="23c6b-106">若要查看可用的行帽, 请<xref:System.Windows.Media.PenLineCap>参阅枚举。</span><span class="sxs-lookup"><span data-stu-id="23c6b-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23c6b-107">此属性仅影响开放形状, 如<xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Polyline>、或打开<xref:System.Windows.Shapes.Path>的元素。</span><span class="sxs-lookup"><span data-stu-id="23c6b-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="23c6b-108">下面的示例绘制四<xref:System.Windows.Shapes.Polyline>个元素, 并在每个元素的两端使用一组不同的形状。</span><span class="sxs-lookup"><span data-stu-id="23c6b-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23c6b-109">示例</span><span class="sxs-lookup"><span data-stu-id="23c6b-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="23c6b-110">此示例摘自一个更大的示例;有关完整示例, 请参阅[形状元素示例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="23c6b-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c6b-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="23c6b-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
