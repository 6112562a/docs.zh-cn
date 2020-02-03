---
title: 向数据绑定 DataGridView 控件添加未绑定列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747068"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="84482-102">如何：将未绑定的列添加到绑定了数据的 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="84482-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="84482-103">在 <xref:System.Windows.Forms.DataGridView> 控件中显示的数据通常来自某种类型的数据源，但你可能需要显示并非来自该数据源的一列数据。</span><span class="sxs-lookup"><span data-stu-id="84482-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="84482-104">这种列称为未绑定列。</span><span class="sxs-lookup"><span data-stu-id="84482-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="84482-105">未绑定列可有多种形式。</span><span class="sxs-lookup"><span data-stu-id="84482-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="84482-106">它们常用于提供对数据行详细信息的访问。</span><span class="sxs-lookup"><span data-stu-id="84482-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="84482-107">下面的代码示例演示了如何创建 "**详细信息**" 按钮的未绑定列，以便在实现主/从方案时显示与父表中的特定行相关的子表。</span><span class="sxs-lookup"><span data-stu-id="84482-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="84482-108">若要响应按钮点击，请实现显示包含子表的窗体的 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="84482-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="84482-109">Visual Studio 中对此任务提供支持。</span><span class="sxs-lookup"><span data-stu-id="84482-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="84482-110">另请参阅[如何：使用设计器在 Windows 窗体 DataGridView 控件中添加和删除列](add-and-remove-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="84482-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84482-111">示例</span><span class="sxs-lookup"><span data-stu-id="84482-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84482-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="84482-112">Compiling the Code</span></span>  
 <span data-ttu-id="84482-113">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="84482-113">This example requires:</span></span>  
  
- <span data-ttu-id="84482-114">名为 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控件。</span><span class="sxs-lookup"><span data-stu-id="84482-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="84482-115">对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="84482-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84482-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84482-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="84482-117">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="84482-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="84482-118">Windows 窗体 DataGridView 控件中的数据显示模式</span><span class="sxs-lookup"><span data-stu-id="84482-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
