---
title: 更改 DataGridView 控件中列的顺序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746542"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3bb93-102">如何：更改 Windows 窗体 DataGridView 控件中列的顺序</span><span class="sxs-lookup"><span data-stu-id="3bb93-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3bb93-103">使用 <xref:System.Windows.Forms.DataGridView> 显示来自数据源的数据时，有时数据源架构中的列不会按你想要显示的顺序显示。</span><span class="sxs-lookup"><span data-stu-id="3bb93-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="3bb93-104">可以通过使用 <xref:System.Windows.Forms.DataGridViewColumn> 类的 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 属性，更改列的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="3bb93-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="3bb93-105">以下代码示例将重新定位绑定到 Northwind 示例数据库中的客户表时自动生成的某些列。</span><span class="sxs-lookup"><span data-stu-id="3bb93-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="3bb93-106">有关如何将 <xref:System.Windows.Forms.DataGridView> 控件绑定到数据库表的详细信息，请参阅[如何：将数据绑定到 Windows 窗体 DataGridView 控件](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb93-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="3bb93-107">Visual Studio 中对此任务提供支持。</span><span class="sxs-lookup"><span data-stu-id="3bb93-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="3bb93-108">另请参阅[如何：使用设计器更改 Windows 窗体 DataGridView 控件中列的顺序](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb93-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bb93-109">示例</span><span class="sxs-lookup"><span data-stu-id="3bb93-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3bb93-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="3bb93-110">Compiling the Code</span></span>  
 <span data-ttu-id="3bb93-111">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="3bb93-111">This example requires:</span></span>  
  
- <span data-ttu-id="3bb93-112">绑定到具有指示列名的表（例如 Northwind 示例数据库中的 `Customers` 表）的、名为 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控件。</span><span class="sxs-lookup"><span data-stu-id="3bb93-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="3bb93-113">对 <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="3bb93-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb93-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bb93-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3bb93-115">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="3bb93-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3bb93-116">如何：将数据绑定到 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="3bb93-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
