---
title: 如何：向文件写入文本
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c637d9842c05f47bfcaa0431dd2f9f1ee29cc09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/28/2018
ms.locfileid: "50181233"
---
# <a name="how-to-write-text-to-a-file"></a>如何：向文件写入文本
本主题展示了针对 .NET Framework 应用程序或 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 应用将文本写入文件的几种不同的方式。 下面的类和方法通常用于将文本写入文件：  
  
-   <xref:System.IO.StreamWriter> - 它包含同步写入文件方法（<xref:System.IO.StreamWriter.Write%2A> 或 <xref:System.IO.TextWriter.WriteLine%2A>或者异步写入文件的方法（<xref:System.IO.StreamWriter.WriteAsync%2A> 和 <xref:System.IO.StreamWriter.WriteLineAsync%2A>。  
  
-   <xref:System.IO.File> – 用于 .NET Framework 应用程序。 它提供了将文本写入文件的静态方法，如 <xref:System.IO.File.WriteAllLines%2A> 和 <xref:System.IO.File.WriteAllText%2A>，或者向文件中追加文本的静态方法（<xref:System.IO.File.AppendAllLines%2A><xref:System.IO.File.AppendAllText%2A> 或 <xref:System.IO.File.AppendText%2A>。  
  
-   <xref:Windows.Storage.FileIO> - 用于 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 应用。 它包含将文本写入文件（<xref:Windows.Storage.FileIO.WriteLinesAsync%2A> 或 <xref:Windows.Storage.FileIO.WriteTextAsync%2A>），或者向文件追加文本（<xref:Windows.Storage.FileIO.AppendLinesAsync%2A> 或 <xref:Windows.Storage.FileIO.AppendTextAsync%2A>的异步方法。  

- <xref:System.IO.Path> - 用于包含文件或目录路径信息的字符串。 它包含可以串联字符串来生成文件或目录路径的 <xref:System.IO.Path.Combine%2A> 方法。


 这些示例都很简单，以便将重点放在正在执行的任务上。 为此，这些示例执行最低限度的错误检查和异常处理（如果有）。 实际的应用程序通常提供更可靠的错误检查和异常处理。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.IO.StreamWriter> 类，一次一行同步地将文本写入新文件。 新文本文件保存到用户的“我的文档”文件夹中。 因为在 <xref:System.IO.StreamWriter> 语句中已声明并实例化 `using` 对象，所以会调用自动刷新并关闭流的 <xref:System.IO.StreamWriter.Dispose%2A> 方法。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.IO.StreamWriter> 类将文本追加到现有的文件。 它使用上一示例中的同一个文本文件。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.IO.StreamWriter> 类异步地将文本写入新文件。 为了调用 <xref:System.IO.StreamWriter.WriteAsync%2A> 方法，方法调用需要在 `async` 方法内。 新文本文件保存到用户的“我的文档”文件夹中。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.IO.File> 类将文本写入新文件并将新的文本行追加到同一文件。 <xref:System.IO.File.WriteAllText%2A> 和 <xref:System.IO.File.AppendAllLines%2A> 方法会自动打开和关闭文件。 如果提供给 <xref:System.IO.File.WriteAllText%2A> 方法的路径已存在，则文件将被覆盖。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何将用户输入异步写入到 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 应用中的一个文本文件。 出于安全考虑，从 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 应用打开文件通常需要使用 <xref:Windows.Storage.Pickers.FileOpenPicker> 控件。 在该示例中，筛选 `FileOpenPicker` 以显示文本文件。  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.Path>  
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
- [如何：枚举目录和文件](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [如何：对新建的数据文件进行读取和写入](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：打开并追加到日志文件](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [如何：从文件读取文本](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [文件和流 I/O](../../../docs/standard/io/index.md)
