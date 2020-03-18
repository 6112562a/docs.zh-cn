---
title: 如何：复制目录
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 5d40db7f902dac8bd6bbdc1510be8e56a321be30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159450"
---
# <a name="how-to-copy-directories"></a>如何：复制目录
此主题演示如何使用 I/O 类将目录下的内容同步复制到另一个位置。

有关异步文件复制的示例，请参阅[异步文件 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。

此示例通过将 `DirectoryCopy` 方法的 `copySubDirs` 设置为 `true` 来复制子目录。 `DirectoryCopy` 方法通过对每个子目录调用其自身的方法来递归复制它们，直到再也没有子目录可以复制为止。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>请参阅

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [文件和流 I/O](../../../docs/standard/io/index.md)
- [通用 I/O 任务](../../../docs/standard/io/common-i-o-tasks.md)
- [异步文件 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)
