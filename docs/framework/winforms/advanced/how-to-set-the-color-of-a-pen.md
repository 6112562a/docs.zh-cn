---
title: 如何：设置笔颜色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: d0402a7d6bb641ef6d97eb41bc25f3c59b3b4250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569435"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="15fb1-102">如何：设置笔颜色</span><span class="sxs-lookup"><span data-stu-id="15fb1-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="15fb1-103">此示例将更改的预先存在的颜色<xref:System.Drawing.Pen>对象</span><span class="sxs-lookup"><span data-stu-id="15fb1-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="15fb1-104">示例</span><span class="sxs-lookup"><span data-stu-id="15fb1-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15fb1-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="15fb1-105">Compiling the Code</span></span>  
 <span data-ttu-id="15fb1-106">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="15fb1-106">This example requires:</span></span>  
  
-   <span data-ttu-id="15fb1-107">一个<xref:System.Drawing.Pen>名为对象`myPen`。</span><span class="sxs-lookup"><span data-stu-id="15fb1-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="15fb1-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="15fb1-108">Robust Programming</span></span>  
 <span data-ttu-id="15fb1-109">应调用<xref:System.Drawing.Pen.Dispose%2A>消耗系统资源的对象 (如<xref:System.Drawing.Pen>对象) 结束使用它们之后。</span><span class="sxs-lookup"><span data-stu-id="15fb1-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15fb1-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="15fb1-110">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="15fb1-111">图形编程入门</span><span class="sxs-lookup"><span data-stu-id="15fb1-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="15fb1-112">如何：创建钢笔</span><span class="sxs-lookup"><span data-stu-id="15fb1-112">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
- [<span data-ttu-id="15fb1-113">使用笔绘制直线和形状</span><span class="sxs-lookup"><span data-stu-id="15fb1-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="15fb1-114">GDI+ 中的笔、直线和矩形</span><span class="sxs-lookup"><span data-stu-id="15fb1-114">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
