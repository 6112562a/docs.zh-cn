---
title: 如何：使用 PLINQ 循环访问文件目录
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 90afc767e422515c6122b8a6ef0e63ffc07caf3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091365"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>如何：使用 PLINQ 循环访问文件目录
此示例展示了两种简单方法，以对文件目录平行执行操作。 第一个查询使用 <xref:System.IO.Directory.GetFiles%2A> 方法，在数组中填充目录和所有子目录中的文件名。 在整个数组填充完成前，此方法不会返回数组，所以可能会在操作开始时引入延迟。 不过，在填充数组后，PLINQ 可以非常快速地并行处理数组。  
  
 第二个查询使用立即开始返回结果的静态 <xref:System.IO.Directory.EnumerateDirectories%2A> 和 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法。 循环访问大型目录树时，这种方法可能会比第一个示例更快，尽管处理时间可能取决于很多因素。  
  
> [!WARNING]
> 这些示例用于演示用法，可能不会比相当的顺序 LINQ to Objects 查询快。 若要详细了解加速，请参阅[了解 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>示例  
 下面的示例展示了如何在以下简单方案中循环访问文件目录：有权访问树中的所有目录，文件大小不是很大，访问时间也不是很长。 这种方法在最初构造文件名数组时有一段延迟。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>示例  
 下面的示例展示了如何在以下简单方案中循环访问文件目录：有权访问树中的所有目录，文件大小不是很大，访问时间也不是很长。 这种方法比上一示例更快地开始生成结果。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 使用 <xref:System.IO.Directory.GetFiles%2A> 时，请确保有权访问树中的所有目录。 否则，将抛出异常，且不会返回任何结果。 如果在 PLINQ 查询中使用 <xref:System.IO.Directory.EnumerateDirectories%2A>，棘手的是合理处理 I/O 异常，以便能够继续循环访问。 如果代码必须处理 I/O 或未经授权的访问异常，应考虑使用[如何：使用并行类循环访问文件目录](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)中介绍的方法。  
  
 如果 I/O 延迟造成问题（例如，对于通过网络的文件 I/O），请考虑使用 [TPL 和传统 .NET Framework 异步编程](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和这篇[博客文章](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)中介绍的异步 I/O 方法之一。  
  
## <a name="see-also"></a>另请参阅

- [并行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
