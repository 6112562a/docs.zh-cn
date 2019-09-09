---
title: 如何：重新排列带分隔符的文件的字段 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 31cb7b936f58653e6223501f3b03cd9472b92453
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253463"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="760af-102">如何：重新排列带分隔符的文件的字段 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="760af-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="760af-103">逗号分隔值 (CSV) 文件是一种文本文件，通常用于存储电子表格数据或其他由行和列表示的表格数据。</span><span class="sxs-lookup"><span data-stu-id="760af-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="760af-104">通过使用 <xref:System.String.Split%2A> 方法分隔字段，可以非常轻松地使用 LINQ 来查询和操作 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="760af-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="760af-105">事实上，可以使用此技术来重新排列任何结构化文本行部分；此技术不局限于 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="760af-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="760af-106">在下面的示例中，假设有三列分别代表学生的“姓氏”、“名字”和“ID”。</span><span class="sxs-lookup"><span data-stu-id="760af-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="760af-107">这些字段基于学生的姓氏按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="760af-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="760af-108">查询生成一个新序列，其中首先出现的是 ID 列，后面的第二列组合了学生的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="760af-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="760af-109">根据 ID 字段重新排列各行。</span><span class="sxs-lookup"><span data-stu-id="760af-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="760af-110">结果保存到新文件，但不修改原始数据。</span><span class="sxs-lookup"><span data-stu-id="760af-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="760af-111">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="760af-111">To create the data file</span></span>  
  
1. <span data-ttu-id="760af-112">将以下各行复制到名为 spreadsheet1.csv 的纯文本文件。</span><span class="sxs-lookup"><span data-stu-id="760af-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="760af-113">将此文件保存到项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="760af-113">Save the file in your project folder.</span></span>  
  
    ```csv  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="760af-114">示例</span><span class="sxs-lookup"><span data-stu-id="760af-114">Example</span></span>  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="760af-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="760af-115">Compiling the Code</span></span>  
<span data-ttu-id="760af-116">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="760af-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="760af-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="760af-117">See also</span></span>

- [<span data-ttu-id="760af-118">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="760af-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="760af-119">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="760af-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="760af-120">如何：从 CSV 文件生成 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="760af-120">How to: Generate XML from CSV Files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
