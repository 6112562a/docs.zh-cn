---
title: 如何：查询目录树中的一个或多个最大的文件 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 20453c754c792d4f5c59fde481e1fec56dcd0e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564118"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="9ab02-102">如何：查询目录树中的一个或多个最大的文件 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab02-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="9ab02-103">此示例演示与文件大小（以字节为单位）相关的五个查询：</span><span class="sxs-lookup"><span data-stu-id="9ab02-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="9ab02-104">如何检索最大文件的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="9ab02-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="9ab02-105">如何检索最小文件的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="9ab02-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="9ab02-106">如何从指定根文件夹下的一个或多个文件夹检索 <xref:System.IO.FileInfo> 对象最大或最小文件。</span><span class="sxs-lookup"><span data-stu-id="9ab02-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="9ab02-107">如何检索序列（如 10 个最大文件）。</span><span class="sxs-lookup"><span data-stu-id="9ab02-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="9ab02-108">如何基于文件大小（以字节为单位）按组对文件进行排序（忽略小于指定大小的文件）。</span><span class="sxs-lookup"><span data-stu-id="9ab02-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab02-109">示例</span><span class="sxs-lookup"><span data-stu-id="9ab02-109">Example</span></span>  
 <span data-ttu-id="9ab02-110">下面的示例包含五个单独的查询，它们演示如何根据文件大小（以字节为单位）对文件进行查询和分组。</span><span class="sxs-lookup"><span data-stu-id="9ab02-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="9ab02-111">可以轻松地修改这些示例，以便使查询基于 <xref:System.IO.FileInfo> 对象的其他某个属性。</span><span class="sxs-lookup"><span data-stu-id="9ab02-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 <span data-ttu-id="9ab02-112">若要返回一个或多个完整的 <xref:System.IO.FileInfo> 对象，查询必须首先检查数据中的每个对象，然后按其 Length 属性值对它们进行排序。</span><span class="sxs-lookup"><span data-stu-id="9ab02-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="9ab02-113">随后它便可以返回具有最大长度的单个对象或对象序列。</span><span class="sxs-lookup"><span data-stu-id="9ab02-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="9ab02-114">使用 <xref:System.Linq.Enumerable.First%2A> 返回列表中的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="9ab02-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="9ab02-115">使用 <xref:System.Linq.Enumerable.Take%2A> 返回前 n 个元素。</span><span class="sxs-lookup"><span data-stu-id="9ab02-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="9ab02-116">指定降序排序顺序可将最小元素置于列表开头。</span><span class="sxs-lookup"><span data-stu-id="9ab02-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="9ab02-117">查询调用单独的方法来获取文件大小（以字节为单位），以便使用在以下情况下会引发的可能异常：自在 `GetFiles` 调用中创建了 <xref:System.IO.FileInfo> 对象以来的时间段内，在其他线程中删除了文件。</span><span class="sxs-lookup"><span data-stu-id="9ab02-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="9ab02-118">即使创建了 <xref:System.IO.FileInfo> 对象，该异常也可能出现，因为 <xref:System.IO.FileInfo> 对象会在首次访问其 <xref:System.IO.FileInfo.Length%2A> 属性时，尝试使用最新大小（以字节为单位）刷新该属性。</span><span class="sxs-lookup"><span data-stu-id="9ab02-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="9ab02-119">通过将此操作置于查询外部的 try-catch 块中，我们可遵循在查询中避免可能导致副作用的操作这一规则。</span><span class="sxs-lookup"><span data-stu-id="9ab02-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="9ab02-120">一般情况下，在使用异常时必须格外谨慎，以确保应用程序不会处于未知状态。</span><span class="sxs-lookup"><span data-stu-id="9ab02-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ab02-121">编译代码</span><span class="sxs-lookup"><span data-stu-id="9ab02-121">Compiling the Code</span></span>  
 <span data-ttu-id="9ab02-122">创建面向 .NET Framework 3.5 或更高版本的项目，此项目包含对 System.Core.dll 的引用和针对 System.Linq 和 System.IO 命名空间的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="9ab02-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab02-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ab02-123">See also</span></span>

- [<span data-ttu-id="9ab02-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab02-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="9ab02-125">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab02-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
