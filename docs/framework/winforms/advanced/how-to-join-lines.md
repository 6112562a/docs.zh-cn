---
title: 如何：联接线
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 55551a78f37a5179b24eda28a9fc5d0a0c640a9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543378"
---
# <a name="how-to-join-lines"></a>如何：联接线
线条联接是由两个线条的端点相交或重叠的常见区域。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了三个行联接样式： 斜接、 凹凸效果，和舍入。 线段联接样式是的一个属性<xref:System.Drawing.Pen>类。 当指定为线段联接样式<xref:System.Drawing.Pen>对象，联接样式，将应用于任何中所有连接的直线<xref:System.Drawing.Drawing2D.GraphicsPath>使用该笔绘制的对象。  
  
 下图显示斜切的线条联接示例的结果。  
  
 ![笔](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>示例  
 可以通过使用指定线段联接样式<xref:System.Drawing.Pen.LineJoin%2A>属性的<xref:System.Drawing.Pen>类。 该示例演示一条水平线和垂直线之间斜角的行联接。 在下面的代码中，值<xref:System.Drawing.Drawing2D.LineJoin.Bevel>分配给<xref:System.Drawing.Pen.LineJoin%2A>属性是的成员<xref:System.Drawing.Drawing2D.LineJoin>枚举。 其他成员<xref:System.Drawing.Drawing2D.LineJoin>枚举都<xref:System.Drawing.Drawing2D.LineJoin.Miter>和<xref:System.Drawing.Drawing2D.LineJoin.Round>。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，后者是 <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。  
  
## <a name="see-also"></a>请参阅
- [使用笔绘制直线和形状](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
