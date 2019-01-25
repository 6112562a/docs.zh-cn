---
title: 如何：对 BorderThickness 值进行动画处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: bd9c75ecb6c95f0dad562701940850e111dddbff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664377"
---
# <a name="how-to-animate-a-borderthickness-value"></a><span data-ttu-id="1238a-102">如何：对 BorderThickness 值进行动画处理</span><span class="sxs-lookup"><span data-stu-id="1238a-102">How to: Animate a BorderThickness Value</span></span>
<span data-ttu-id="1238a-103">此示例演示如何使用更改对边框的粗细进行动画处理<xref:System.Windows.Media.Animation.ThicknessAnimation>类。</span><span class="sxs-lookup"><span data-stu-id="1238a-103">This example shows how to animate changes to the thickness of a border by using the <xref:System.Windows.Media.Animation.ThicknessAnimation> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1238a-104">示例</span><span class="sxs-lookup"><span data-stu-id="1238a-104">Example</span></span>  
 <span data-ttu-id="1238a-105">下面的示例通过使用进行动画处理对边框的粗细<xref:System.Windows.Media.Animation.ThicknessAnimation>。</span><span class="sxs-lookup"><span data-stu-id="1238a-105">The following example animates the thickness of a border by using <xref:System.Windows.Media.Animation.ThicknessAnimation>.</span></span> <span data-ttu-id="1238a-106">该示例使用<xref:System.Windows.Controls.Border.BorderThickness%2A>属性的<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="1238a-106">The example uses the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 <span data-ttu-id="1238a-107">有关完整示例，请参阅[动画示例库](https://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="1238a-107">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1238a-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="1238a-108">See also</span></span>
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [<span data-ttu-id="1238a-109">动画概述</span><span class="sxs-lookup"><span data-stu-id="1238a-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="1238a-110">动画和计时</span><span class="sxs-lookup"><span data-stu-id="1238a-110">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="1238a-111">帮助主题</span><span class="sxs-lookup"><span data-stu-id="1238a-111">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="1238a-112">使用关键帧为边框粗细设置动画效果</span><span class="sxs-lookup"><span data-stu-id="1238a-112">Animate the Thickness of a Border by Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
