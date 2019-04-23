---
title: 创建 AutoIncrement 列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 99c52b93cee858511d50aba2f30f2b9f96d91ccd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090935"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="d58fd-102">创建 AutoIncrement 列</span><span class="sxs-lookup"><span data-stu-id="d58fd-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="d58fd-103">要确保列值的唯一，可将列值设置为在表中添加新行时自动递增。</span><span class="sxs-lookup"><span data-stu-id="d58fd-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="d58fd-104">若要创建自动递增<xref:System.Data.DataColumn>，将<xref:System.Data.DataColumn.AutoIncrement%2A>属性的列**true**。</span><span class="sxs-lookup"><span data-stu-id="d58fd-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="d58fd-105"><xref:System.Data.DataColumn>中定义的值然后开始<xref:System.Data.DataColumn.AutoIncrementSeed%2A>属性，与每个行添加的值**AutoIncrement**列中定义的值会增加<xref:System.Data.DataColumn.AutoIncrementStep%2A>的列的属性。</span><span class="sxs-lookup"><span data-stu-id="d58fd-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="d58fd-106">有关**AutoIncrement**列，我们建议，<xref:System.Data.DataColumn.ReadOnly%2A>的属性**DataColumn**设置为**true**。</span><span class="sxs-lookup"><span data-stu-id="d58fd-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="d58fd-107">以下示例演示了如何创建从值 200 开始并以 3 为增量递增的列。</span><span class="sxs-lookup"><span data-stu-id="d58fd-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d58fd-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="d58fd-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="d58fd-109">数据表架构定义</span><span class="sxs-lookup"><span data-stu-id="d58fd-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="d58fd-110">数据表</span><span class="sxs-lookup"><span data-stu-id="d58fd-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="d58fd-111">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="d58fd-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
