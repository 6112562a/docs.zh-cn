---
title: 如何：对矩形进行动画处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: d164a6ecc64c1a4e78be41304cace7515684b488
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530093"
---
# <a name="how-to-animate-a-rectangle"></a>如何：对矩形进行动画处理
此示例演示如何对矩形的大小和位置变化进行动画处理。  
  
## <a name="example"></a>示例  
 下面的示例使用的实例<xref:System.Windows.Media.Animation.RectAnimation>类进行动画处理<xref:System.Windows.Media.RectangleGeometry.Rect%2A>属性的<xref:System.Windows.Media.RectangleGeometry>，其更改的大小和位置的矩形进行动画处理。  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [动画概述](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [图形和多媒体](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [帮助主题](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)
- [动画和计时](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [帮助主题](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
