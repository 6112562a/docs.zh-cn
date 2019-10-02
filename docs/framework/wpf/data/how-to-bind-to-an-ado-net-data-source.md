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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="f6bec-102">如何：绑定到 ADO.NET 数据源</span><span class="sxs-lookup"><span data-stu-id="f6bec-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="f6bec-103">此示例演示如何将 @no__t 0 @no__t 控件绑定到 ADO.NET @no__t。</span><span class="sxs-lookup"><span data-stu-id="f6bec-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="f6bec-104">示例</span><span class="sxs-lookup"><span data-stu-id="f6bec-104">Example</span></span>

<span data-ttu-id="f6bec-105">在本示例中，`OleDbConnection` 对象用于连接到数据源，该数据源是在连接字符串中指定的 `Access MDB` 文件。</span><span class="sxs-lookup"><span data-stu-id="f6bec-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="f6bec-106">建立连接后，会创建一个 `OleDbDataAdapter` 对象。</span><span class="sxs-lookup"><span data-stu-id="f6bec-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="f6bec-107">@No__t 0 对象执行 select 结构化查询语言（SQL）语句以从数据库中检索记录集。</span><span class="sxs-lookup"><span data-stu-id="f6bec-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="f6bec-108">SQL 命令的结果存储在 @no__t 的 @no__t 0 中，通过调用 @no__t 的 `Fill` 方法。</span><span class="sxs-lookup"><span data-stu-id="f6bec-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="f6bec-109">本示例中，`DataTable` 命名为 `BookTable`。</span><span class="sxs-lookup"><span data-stu-id="f6bec-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="f6bec-110">然后，该示例将 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 属性设置为 `DataSet` 对象。</span><span class="sxs-lookup"><span data-stu-id="f6bec-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="f6bec-111">然后，我们可以将 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性绑定到 `DataSet` 的 `BookTable`:</span><span class="sxs-lookup"><span data-stu-id="f6bec-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="f6bec-112">`BookItemTemplate` 是定义数据显示方式的 <xref:System.Windows.DataTemplate>：</span><span class="sxs-lookup"><span data-stu-id="f6bec-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="f6bec-113">`IntColorConverter` 将 `int` 转换为颜色。</span><span class="sxs-lookup"><span data-stu-id="f6bec-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="f6bec-114">通过使用此转换器，如果 `NumPages` 的值小于 350，第三个 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Background%2A> 颜色将显示为绿色，否则为红色。</span><span class="sxs-lookup"><span data-stu-id="f6bec-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="f6bec-115">此处未展示该转换器的实现。</span><span class="sxs-lookup"><span data-stu-id="f6bec-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6bec-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6bec-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="f6bec-117">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="f6bec-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="f6bec-118">帮助主题</span><span class="sxs-lookup"><span data-stu-id="f6bec-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
