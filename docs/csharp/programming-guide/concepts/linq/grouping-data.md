---
title: 对数据分组 (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: e7f10b121a7a1c599d88731a806fe784eb1a7e66
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423408"
---
# <a name="grouping-data-c"></a><span data-ttu-id="84706-102">对数据分组 (C#)</span><span class="sxs-lookup"><span data-stu-id="84706-102">Grouping Data (C#)</span></span>
<span data-ttu-id="84706-103">分组是指将数据分到不同的组，使每组中的元素拥有公共的属性。</span><span class="sxs-lookup"><span data-stu-id="84706-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="84706-104">下图演示了对字符序列进行分组的结果。</span><span class="sxs-lookup"><span data-stu-id="84706-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="84706-105">每个组的键是字符。</span><span class="sxs-lookup"><span data-stu-id="84706-105">The key for each group is the character.</span></span>  
  
 ![关系图显示 LINQ 分组操作。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="84706-107">下一节列出了对数据元素进行分组的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="84706-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84706-108">方法</span><span class="sxs-lookup"><span data-stu-id="84706-108">Methods</span></span>  
  
|<span data-ttu-id="84706-109">方法名</span><span class="sxs-lookup"><span data-stu-id="84706-109">Method Name</span></span>|<span data-ttu-id="84706-110">说明</span><span class="sxs-lookup"><span data-stu-id="84706-110">Description</span></span>|<span data-ttu-id="84706-111">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="84706-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="84706-112">详细信息</span><span class="sxs-lookup"><span data-stu-id="84706-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="84706-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="84706-113">GroupBy</span></span>|<span data-ttu-id="84706-114">对共享通用属性的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="84706-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="84706-115">每组由一个 <xref:System.Linq.IGrouping%602> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="84706-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="84706-116">-或-</span><span class="sxs-lookup"><span data-stu-id="84706-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84706-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="84706-117">ToLookup</span></span>|<span data-ttu-id="84706-118">将元素插入基于键选择器函数的 <xref:System.Linq.Lookup%602>（一种一对多字典）。</span><span class="sxs-lookup"><span data-stu-id="84706-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="84706-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="84706-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="84706-120">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="84706-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="84706-121">下列代码示例根据奇偶性，使用 `group by` 子句对列表中的整数进行分组。</span><span class="sxs-lookup"><span data-stu-id="84706-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="84706-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="84706-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="84706-123">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="84706-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="84706-124">group 子句</span><span class="sxs-lookup"><span data-stu-id="84706-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="84706-125">如何：创建嵌套组</span><span class="sxs-lookup"><span data-stu-id="84706-125">How to: Create a Nested Group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="84706-126">如何：按扩展名对文件进行分组 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="84706-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="84706-127">如何：对查询结果进行分组</span><span class="sxs-lookup"><span data-stu-id="84706-127">How to: Group Query Results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="84706-128">如何：对分组操作执行子查询</span><span class="sxs-lookup"><span data-stu-id="84706-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="84706-129">如何：使用组将一个文件拆分成多个文件 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="84706-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
