---
title: 对数据进行分组 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: c658ac5c46baec1bfa976074b78ac86d791b6515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842049"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="07cc5-102">对数据进行分组 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07cc5-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="07cc5-103">分组是指将数据分到不同的组，使每组中的元素拥有公共的属性。</span><span class="sxs-lookup"><span data-stu-id="07cc5-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="07cc5-104">下图演示了对字符序列进行分组的结果。</span><span class="sxs-lookup"><span data-stu-id="07cc5-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="07cc5-105">每个组的键是字符。</span><span class="sxs-lookup"><span data-stu-id="07cc5-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="07cc5-106">![LINQ 分组操作](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="07cc5-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="07cc5-107">下一节列出了对数据元素进行分组的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="07cc5-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07cc5-108">方法</span><span class="sxs-lookup"><span data-stu-id="07cc5-108">Methods</span></span>  
  
|<span data-ttu-id="07cc5-109">方法名</span><span class="sxs-lookup"><span data-stu-id="07cc5-109">Method Name</span></span>|<span data-ttu-id="07cc5-110">描述</span><span class="sxs-lookup"><span data-stu-id="07cc5-110">Description</span></span>|<span data-ttu-id="07cc5-111">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="07cc5-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="07cc5-112">详细信息</span><span class="sxs-lookup"><span data-stu-id="07cc5-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="07cc5-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="07cc5-113">GroupBy</span></span>|<span data-ttu-id="07cc5-114">对共享通用属性的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="07cc5-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="07cc5-115">每组由一个 <xref:System.Linq.IGrouping%602> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="07cc5-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="07cc5-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="07cc5-116">ToLookup</span></span>|<span data-ttu-id="07cc5-117">将元素插入基于键选择器函数的 <xref:System.Linq.Lookup%602>（一种一对多字典）。</span><span class="sxs-lookup"><span data-stu-id="07cc5-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="07cc5-118">不适用。</span><span class="sxs-lookup"><span data-stu-id="07cc5-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="07cc5-119">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="07cc5-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="07cc5-120">下列代码示例根据奇偶性，使用 `Group By` 子句对列表中的整数进行分组。</span><span class="sxs-lookup"><span data-stu-id="07cc5-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="07cc5-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="07cc5-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="07cc5-122">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07cc5-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="07cc5-123">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="07cc5-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="07cc5-124">如何：文件分组依据扩展 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07cc5-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="07cc5-125">如何：使用组 (LINQ) (Visual Basic 中) 将一个文件拆分成多个文件</span><span class="sxs-lookup"><span data-stu-id="07cc5-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
