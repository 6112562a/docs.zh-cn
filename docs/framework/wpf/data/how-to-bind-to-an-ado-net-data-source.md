---
title: 如何：绑定到 ADO.NET 数据源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697144"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>如何：绑定到 ADO.NET 数据源

此示例演示如何将 @no__t 0 @no__t 控件绑定到 ADO.NET @no__t。

## <a name="example"></a>示例

在本示例中，`OleDbConnection` 对象用于连接到数据源，该数据源是在连接字符串中指定的 `Access MDB` 文件。 建立连接后，会创建一个 `OleDbDataAdapter` 对象。 @No__t 0 对象执行 select 结构化查询语言（SQL）语句以从数据库中检索记录集。 SQL 命令的结果存储在 @no__t 的 @no__t 0 中，通过调用 @no__t 的 `Fill` 方法。 本示例中，`DataTable` 命名为 `BookTable`。 然后，该示例将 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 属性设置为 `DataSet` 对象。

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

然后，我们可以将 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性绑定到 `DataSet` 的 `BookTable`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` 是定义数据显示方式的 <xref:System.Windows.DataTemplate>：

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` 将 `int` 转换为颜色。 通过使用此转换器，如果 `NumPages` 的值小于 350，第三个 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Background%2A> 颜色将显示为绿色，否则为红色。 此处未展示该转换器的实现。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Data.BindingListCollectionView>
- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
