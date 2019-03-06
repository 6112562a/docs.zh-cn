---
title: 如何：使对象跟随鼠标指针移动
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 6b86cadba19e82c487be88bcfb08edb51f93c540
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358296"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="6aa8e-102">如何：使对象跟随鼠标指针移动</span><span class="sxs-lookup"><span data-stu-id="6aa8e-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="6aa8e-103">此示例演示如何在屏幕上移动鼠标指针时更改对象的维度。</span><span class="sxs-lookup"><span data-stu-id="6aa8e-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="6aa8e-104">该示例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]创建的文件[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]和创建事件处理程序的代码隐藏文件。</span><span class="sxs-lookup"><span data-stu-id="6aa8e-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa8e-105">示例</span><span class="sxs-lookup"><span data-stu-id="6aa8e-105">Example</span></span>  
 <span data-ttu-id="6aa8e-106">以下[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]创建[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，其中包括<xref:System.Windows.Shapes.Ellipse>内<xref:System.Windows.Controls.StackPanel>，并将附加的事件处理程序<xref:System.Windows.UIElement.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="6aa8e-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="6aa8e-107">下面的代码隐藏创建<xref:System.Windows.UIElement.MouseMove>事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6aa8e-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="6aa8e-108">当鼠标指针移动，高度和宽度<xref:System.Windows.Shapes.Ellipse>增加和减少。</span><span class="sxs-lookup"><span data-stu-id="6aa8e-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="6aa8e-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="6aa8e-109">See also</span></span>
- [<span data-ttu-id="6aa8e-110">输入概述</span><span class="sxs-lookup"><span data-stu-id="6aa8e-110">Input Overview</span></span>](input-overview.md)
