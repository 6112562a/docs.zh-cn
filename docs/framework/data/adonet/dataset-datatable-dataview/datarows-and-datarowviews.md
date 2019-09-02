---
title: DataRow 和 DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205089"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="a052f-102">DataRow 和 DataRowView</span><span class="sxs-lookup"><span data-stu-id="a052f-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="a052f-103"><xref:System.Data.DataView> 公开 <xref:System.Data.DataRowView> 对象的可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="a052f-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="a052f-104">**DataRowView**对象将值公开为按基础表中的列的名称或序号引用进行索引的对象数组。</span><span class="sxs-lookup"><span data-stu-id="a052f-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="a052f-105">可以使用<xref:System.Data.DataRow> **DataRowView 的** **属性访问由 DataRowView**公开的。 <xref:System.Data.DataRowView.Row%2A></span><span class="sxs-lookup"><span data-stu-id="a052f-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="a052f-106">使用**DataRowView**查看值时, <xref:System.Data.DataView.RowStateFilter%2A> **DataView**的属性将确定公开基础**DataRow**的行版本。</span><span class="sxs-lookup"><span data-stu-id="a052f-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="a052f-107">有关使用**DataRow**访问不同行版本的信息, 请参阅[行状态和行版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="a052f-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="a052f-108">以下代码示例显示一个表中的所有当前值和原始值。</span><span class="sxs-lookup"><span data-stu-id="a052f-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a052f-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="a052f-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="a052f-110">数据视图</span><span class="sxs-lookup"><span data-stu-id="a052f-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="a052f-111">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="a052f-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
