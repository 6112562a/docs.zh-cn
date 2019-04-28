---
title: 查询类型化数据集
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651735"
---
# <a name="query-typed-datasets"></a>查询类型化数据集

如果的架构<xref:System.Data.DataSet>在应用程序设计时已知，我们建议你使用类型化<xref:System.Data.DataSet>时使用 LINQ to DataSet。 类型化 <xref:System.Data.DataSet> 是从 <xref:System.Data.DataSet> 中派生的类。 因此，它继承 <xref:System.Data.DataSet> 的所有方法、事件和属性。 此外，类型化 <xref:System.Data.DataSet> 还提供强类型方法、事件和属性。 这意味着可以按名称而不使用基于集合的方法来访问表和列。 这可使查询更简单、更具可读性。 有关详细信息，请参阅[类型化数据集](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。

LINQ to DataSet 还支持对类型化查询<xref:System.Data.DataSet>。 对于类型化 <xref:System.Data.DataSet>，您不必使用泛型 <xref:System.Data.DataRowExtensions.Field%2A> 方法或 <xref:System.Data.DataRowExtensions.SetField%2A> 方法即可访问列数据。 由于 <xref:System.Data.DataSet> 中包括类型信息，因此属性名称在编译时可用。 LINQ 到数据集作为正确类型，提供到列的值的访问，以便在编译代码而不是在运行时捕获类型不匹配错误。

你可以开始查询类型化之前<xref:System.Data.DataSet>，必须通过使用生成该类**数据集设计器**Visual Studio 中。 有关详细信息，请参阅[创建和配置数据集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。

## <a name="example"></a>示例

下面的示例演示对类型化 <xref:System.Data.DataSet> 进行查询：

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>请参阅

- [查询数据集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [跨表查询](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [单表查询](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
