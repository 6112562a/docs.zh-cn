---
title: 在 DataGridView 控件中隐藏列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 7ac6ccac5c02f014d5aa629956e51675cc60fddc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736561"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="72690-102">如何：隐藏 Windows 窗体 DataGridView 控件中的列</span><span class="sxs-lookup"><span data-stu-id="72690-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="72690-103">有时，你会想仅显示在 Windows 窗体 <xref:System.Windows.Forms.DataGridView> 控件中可用的某些列。</span><span class="sxs-lookup"><span data-stu-id="72690-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="72690-104">例如，你或许想对具有管理凭据的用户显示雇员的工资列，但却对其他用户隐藏。</span><span class="sxs-lookup"><span data-stu-id="72690-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="72690-105">或者，你或许想将控件绑定到包含若干列的数据源，但其中仅有一部分是你想显示的列。</span><span class="sxs-lookup"><span data-stu-id="72690-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="72690-106">这种情况下，你通常会移除不想显示的列，而不是隐藏它们。</span><span class="sxs-lookup"><span data-stu-id="72690-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="72690-107">在 <xref:System.Windows.Forms.DataGridView> 控件，列的 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 属性值确定是否显示该列。</span><span class="sxs-lookup"><span data-stu-id="72690-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="72690-108">Visual Studio 中对此任务提供支持。</span><span class="sxs-lookup"><span data-stu-id="72690-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="72690-109">另请参阅[如何：使用设计器在 Windows 窗体 DataGridView 控件中隐藏列](hide-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="72690-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="72690-110">若要以编程方式隐藏某一列</span><span class="sxs-lookup"><span data-stu-id="72690-110">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="72690-111">将 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="72690-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="72690-112">若要隐藏数据绑定时自动生成的 `CustomerID` 列，请将下面的代码示例放置在 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 事件处理程序中。</span><span class="sxs-lookup"><span data-stu-id="72690-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72690-113">编译代码</span><span class="sxs-lookup"><span data-stu-id="72690-113">Compiling the Code</span></span>  
 <span data-ttu-id="72690-114">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="72690-114">This example requires:</span></span>  
  
- <span data-ttu-id="72690-115">名为 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控件，其包含一个名为 `CustomerID` 的列。</span><span class="sxs-lookup"><span data-stu-id="72690-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="72690-116">对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="72690-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72690-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72690-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="72690-118">Windows 窗体 DataGridView 控件中的列、行和单元格基本功能</span><span class="sxs-lookup"><span data-stu-id="72690-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="72690-119">如何：从 Windows 窗体 DataGridView 控件中删除自动生成的列</span><span class="sxs-lookup"><span data-stu-id="72690-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="72690-120">如何：在 Windows 窗体 DataGridView 控件中更改列顺序</span><span class="sxs-lookup"><span data-stu-id="72690-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
