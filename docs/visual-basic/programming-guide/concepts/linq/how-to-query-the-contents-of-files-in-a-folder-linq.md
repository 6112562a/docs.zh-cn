---
title: 如何：查询 (LINQ) (Visual Basic 中) 的文件夹中的文件的内容
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 6bebb4bd7444516c51551a5c56171d08f9d0ef2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566915"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="a7feb-102">如何：查询 (LINQ) (Visual Basic 中) 的文件夹中的文件的内容</span><span class="sxs-lookup"><span data-stu-id="a7feb-102">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="a7feb-103">此示例演示如何查询指定目录树中的所有文件、打开每个文件并检查其内容。</span><span class="sxs-lookup"><span data-stu-id="a7feb-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="a7feb-104">此类技术可用于对目录树的内容创建索引或反向索引。</span><span class="sxs-lookup"><span data-stu-id="a7feb-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="a7feb-105">此示例中执行的是简单的字符串搜索。</span><span class="sxs-lookup"><span data-stu-id="a7feb-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="a7feb-106">但是，可使用正则表达式执行类型更复杂的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="a7feb-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="a7feb-107">有关详细信息，请参阅[如何：将 LINQ 查询与正则表达式 (Visual Basic) 合并](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a7feb-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7feb-108">示例</span><span class="sxs-lookup"><span data-stu-id="a7feb-108">Example</span></span>  
  
```vb  
Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "c:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        Dim searchTerm = "Visual Studio"  
  
        ' Search the contents of each file.  
        ' A regular expression created with the RegEx class  
        ' could be used instead of the Contains method.  
        Dim queryMatchingFiles = From file In fileList _  
                                 Where file.Extension = ".htm" _  
                                 Let fileText = GetFileText(file.FullName) _  
                                 Where fileText.Contains(searchTerm) _  
                                 Select file.FullName  
  
        Console.WriteLine("The term " & searchTerm & " was found in:")  
  
        ' Execute the query.  
        For Each filename In queryMatchingFiles  
            Console.WriteLine(filename)  
        Next  
  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit")  
        Console.ReadKey()  
  
    End Sub  
  
    ' Read the contents of the file. This is done in a separate  
    ' function in order to handle potential file system errors.  
    Function GetFileText(ByVal name As String) As String  
  
        ' If the file has been deleted, the right thing  
        ' to do in this case is return an empty string.  
        Dim fileContents = String.Empty  
  
        ' If the file has been deleted since we took   
        ' the snapshot, ignore it and return the empty string.  
        If System.IO.File.Exists(name) Then  
            fileContents = System.IO.File.ReadAllText(name)  
        End If  
  
        Return fileContents  
  
    End Function  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7feb-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="a7feb-109">Compiling the Code</span></span>  
 <span data-ttu-id="a7feb-110">创建面向 .NET Framework 3.5 或更高版本的项目，此项目包含对 System.Core.dll 的引用和用于 System.Linq 命名空间的 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="a7feb-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7feb-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7feb-111">See also</span></span>
- [<span data-ttu-id="a7feb-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7feb-112">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="a7feb-113">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7feb-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
