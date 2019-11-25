---
title: 如何：查找两个列表之间的差集 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 9e2a42a466a71d4e351df89398be197197a54042
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140989"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="4b344-102">如何：查找两个列表之间的差集 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b344-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="4b344-103">此示例演示如何使用 LINQ 对两个字符串列表进行比较，并输出那些位于 names1.txt 中但不在 names2.txt 中的行。</span><span class="sxs-lookup"><span data-stu-id="4b344-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="4b344-104">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="4b344-104">To create the data files</span></span>  
  
1. <span data-ttu-id="4b344-105">按照[如何合并和比较字符串集合 (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md) 中的说明，将 names1.txt 和 names2.txt 复制到解决方案文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4b344-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b344-106">示例</span><span class="sxs-lookup"><span data-stu-id="4b344-106">Example</span></span>  
  
```csharp  
class CompareLists  
{          
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="4b344-107">C# 中某些类型的查询操作（例如 <xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A>）只能用基于方法的语法表示。</span><span class="sxs-lookup"><span data-stu-id="4b344-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b344-108">编译代码</span><span class="sxs-lookup"><span data-stu-id="4b344-108">Compiling the Code</span></span>  
 <span data-ttu-id="4b344-109">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="4b344-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b344-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b344-110">See also</span></span>

- [<span data-ttu-id="4b344-111">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b344-111">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
