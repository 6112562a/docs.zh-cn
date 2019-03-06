---
title: 如何：使动画加速或减速
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: d4fcaf4a684c37590f27d603ef5cb2c86a6fb854
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376242"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="2863c-102">如何：使动画加速或减速</span><span class="sxs-lookup"><span data-stu-id="2863c-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="2863c-103">此示例演示如何使动画加速和减速随着时间的推移。</span><span class="sxs-lookup"><span data-stu-id="2863c-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="2863c-104">在以下示例中，多个矩形进行动画处理与不同的动画<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>和<xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>设置。</span><span class="sxs-lookup"><span data-stu-id="2863c-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2863c-105">示例</span><span class="sxs-lookup"><span data-stu-id="2863c-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="2863c-106">此示例中省略了代码。</span><span class="sxs-lookup"><span data-stu-id="2863c-106">Code has been omitted from this example.</span></span> <span data-ttu-id="2863c-107">有关完整的代码，请参阅[动画计时行为 (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp)或[动画计时行为 (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)。</span><span class="sxs-lookup"><span data-stu-id="2863c-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
