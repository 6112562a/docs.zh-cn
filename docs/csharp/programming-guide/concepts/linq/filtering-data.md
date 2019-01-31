---
title: 筛选数据 (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: dc31a73a8ebbe52f7d22984cd747a038e2556c28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634631"
---
# <a name="filtering-data-c"></a><span data-ttu-id="852d9-102">筛选数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="852d9-102">Filtering Data (C#)</span></span>
<span data-ttu-id="852d9-103">筛选是指将结果集限制为仅包含满足指定条件的元素的操作。</span><span class="sxs-lookup"><span data-stu-id="852d9-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="852d9-104">它也称为选定内容。</span><span class="sxs-lookup"><span data-stu-id="852d9-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="852d9-105">下图演示了对字符序列进行筛选的结果。</span><span class="sxs-lookup"><span data-stu-id="852d9-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="852d9-106">筛选操作的谓词指定字符必须为“A”。</span><span class="sxs-lookup"><span data-stu-id="852d9-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="852d9-107">![LINQ 筛选操作](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="852d9-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="852d9-108">下面一节列出了执行所选内容的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="852d9-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="852d9-109">方法</span><span class="sxs-lookup"><span data-stu-id="852d9-109">Methods</span></span>  
  
|<span data-ttu-id="852d9-110">方法名</span><span class="sxs-lookup"><span data-stu-id="852d9-110">Method Name</span></span>|<span data-ttu-id="852d9-111">说明</span><span class="sxs-lookup"><span data-stu-id="852d9-111">Description</span></span>|<span data-ttu-id="852d9-112">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="852d9-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="852d9-113">详细信息</span><span class="sxs-lookup"><span data-stu-id="852d9-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="852d9-114">OfType</span><span class="sxs-lookup"><span data-stu-id="852d9-114">OfType</span></span>|<span data-ttu-id="852d9-115">根据其转换为特定类型的能力选择值。</span><span class="sxs-lookup"><span data-stu-id="852d9-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="852d9-116">不适用。</span><span class="sxs-lookup"><span data-stu-id="852d9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="852d9-117">Where</span><span class="sxs-lookup"><span data-stu-id="852d9-117">Where</span></span>|<span data-ttu-id="852d9-118">选择基于谓词函数的值。</span><span class="sxs-lookup"><span data-stu-id="852d9-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="852d9-119">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="852d9-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="852d9-120">以下示例使用 `where` 子句从数组中筛选具有特定长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="852d9-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="852d9-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="852d9-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="852d9-122">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="852d9-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="852d9-123">where 子句</span><span class="sxs-lookup"><span data-stu-id="852d9-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="852d9-124">如何：在运行时动态指定谓词筛选器</span><span class="sxs-lookup"><span data-stu-id="852d9-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="852d9-125">如何：使用反射查询程序集的元数据 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="852d9-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="852d9-126">如何：查询具有指定特性或名称的文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="852d9-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="852d9-127">如何：按任意词或字段对文本数据进行排序或筛选 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="852d9-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
