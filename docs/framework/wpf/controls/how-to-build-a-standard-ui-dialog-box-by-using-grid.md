---
title: 如何：使用 Grid 生成标准 UI 对话框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051047"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="df0c3-102">如何：使用 Grid 生成标准 UI 对话框</span><span class="sxs-lookup"><span data-stu-id="df0c3-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="df0c3-103">此示例演示如何创建标准[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]对话框中，通过使用<xref:System.Windows.Controls.Grid>元素。</span><span class="sxs-lookup"><span data-stu-id="df0c3-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0c3-104">示例</span><span class="sxs-lookup"><span data-stu-id="df0c3-104">Example</span></span>  
 <span data-ttu-id="df0c3-105">下面的示例创建像那样的对话框**运行**中的对话框[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]操作系统。</span><span class="sxs-lookup"><span data-stu-id="df0c3-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="df0c3-106">此示例将创建<xref:System.Windows.Controls.Grid>，并使用<xref:System.Windows.Controls.ColumnDefinition>和<xref:System.Windows.Controls.RowDefinition>类来定义五个列和四个行。</span><span class="sxs-lookup"><span data-stu-id="df0c3-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="df0c3-107">该示例然后添加并将置于<xref:System.Windows.Controls.Image>， `RunIcon.png`，用于表示在对话框中找到的映像。</span><span class="sxs-lookup"><span data-stu-id="df0c3-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="df0c3-108">图像被置于中第一列和行的<xref:System.Windows.Controls.Grid>（左上角）。</span><span class="sxs-lookup"><span data-stu-id="df0c3-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="df0c3-109">接下来，该示例将添加<xref:System.Windows.Controls.TextBlock>跨越第一行的剩余列的第一列的元素。</span><span class="sxs-lookup"><span data-stu-id="df0c3-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="df0c3-110">它将添加另一个<xref:System.Windows.Controls.TextBlock>元素来表示第一列中的第二个行**打开**文本框。</span><span class="sxs-lookup"><span data-stu-id="df0c3-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="df0c3-111">一个<xref:System.Windows.Controls.TextBlock>如下所示，它表示数据输入区域。</span><span class="sxs-lookup"><span data-stu-id="df0c3-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="df0c3-112">最后，该示例将添加三个<xref:System.Windows.Controls.Button>针对最后一行的元素，后者表示**确定**，**取消**，并且**浏览**事件。</span><span class="sxs-lookup"><span data-stu-id="df0c3-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="df0c3-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="df0c3-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="df0c3-114">面板概述</span><span class="sxs-lookup"><span data-stu-id="df0c3-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="df0c3-115">帮助主题</span><span class="sxs-lookup"><span data-stu-id="df0c3-115">How-to Topics</span></span>](grid-how-to-topics.md)
