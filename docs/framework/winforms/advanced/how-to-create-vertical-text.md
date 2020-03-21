---
title: 如何：创建垂直文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182558"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="08644-102">如何：创建垂直文本</span><span class="sxs-lookup"><span data-stu-id="08644-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="08644-103">可以使用<xref:System.Drawing.StringFormat>对象指定垂直而不是水平绘制文本。</span><span class="sxs-lookup"><span data-stu-id="08644-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08644-104">示例</span><span class="sxs-lookup"><span data-stu-id="08644-104">Example</span></span>  
 <span data-ttu-id="08644-105">下面的示例将该值<xref:System.Drawing.StringFormatFlags.DirectionVertical>分配给<xref:System.Drawing.StringFormat.FormatFlags%2A><xref:System.Drawing.StringFormat>对象的属性。</span><span class="sxs-lookup"><span data-stu-id="08644-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="08644-106">该<xref:System.Drawing.StringFormat>对象传递给<xref:System.Drawing.Graphics.DrawString%2A><xref:System.Drawing.Graphics>类的方法。</span><span class="sxs-lookup"><span data-stu-id="08644-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="08644-107">该值<xref:System.Drawing.StringFormatFlags.DirectionVertical>是枚举的成员<xref:System.Drawing.StringFormatFlags>。</span><span class="sxs-lookup"><span data-stu-id="08644-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="08644-108">下图显示了垂直文本：</span><span class="sxs-lookup"><span data-stu-id="08644-108">The following illustration shows the vertical text:</span></span>
  
 ![显示垂直字体文本的图形。](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08644-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="08644-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="08644-111">前面的示例设计用于 Windows 窗体，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler></span><span class="sxs-lookup"><span data-stu-id="08644-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08644-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08644-112">See also</span></span>

- [<span data-ttu-id="08644-113">如何：用 GDI 绘制文本</span><span class="sxs-lookup"><span data-stu-id="08644-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
