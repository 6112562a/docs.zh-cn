---
title: 数据分区
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353154"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="2309d-102">Partitioning Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2309d-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="2309d-103">LINQ 中的分区是指将输入序列划分为两个部分的操作，无需重新排列元素，然后返回其中一个部分。</span><span class="sxs-lookup"><span data-stu-id="2309d-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="2309d-104">下图显示对字符序列进行三种不同的分区操作的结果。</span><span class="sxs-lookup"><span data-stu-id="2309d-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="2309d-105">第一个操作返回序列中的前三个元素。</span><span class="sxs-lookup"><span data-stu-id="2309d-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="2309d-106">第二个操作跳过前三个元素，返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="2309d-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="2309d-107">第三个操作跳过序列中的前两个元素，返回接下来的三个元素。</span><span class="sxs-lookup"><span data-stu-id="2309d-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![显示三个 LINQ 分区操作的图示。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="2309d-109">下面一节列出了对序列进行分区的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="2309d-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="2309d-110">运算符</span><span class="sxs-lookup"><span data-stu-id="2309d-110">Operators</span></span>  
  
|<span data-ttu-id="2309d-111">运算符名称</span><span class="sxs-lookup"><span data-stu-id="2309d-111">Operator Name</span></span>|<span data-ttu-id="2309d-112">描述</span><span class="sxs-lookup"><span data-stu-id="2309d-112">Description</span></span>|<span data-ttu-id="2309d-113">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="2309d-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2309d-114">详细信息</span><span class="sxs-lookup"><span data-stu-id="2309d-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="2309d-115">Skip</span><span class="sxs-lookup"><span data-stu-id="2309d-115">Skip</span></span>|<span data-ttu-id="2309d-116">跳过序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="2309d-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2309d-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="2309d-117">SkipWhile</span></span>|<span data-ttu-id="2309d-118">基于谓词函数跳过元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="2309d-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2309d-119">Take</span><span class="sxs-lookup"><span data-stu-id="2309d-119">Take</span></span>|<span data-ttu-id="2309d-120">获取序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="2309d-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2309d-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="2309d-121">TakeWhile</span></span>|<span data-ttu-id="2309d-122">基于谓词函数获取元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="2309d-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="2309d-123">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="2309d-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="2309d-124">Skip</span><span class="sxs-lookup"><span data-stu-id="2309d-124">Skip</span></span>  
 <span data-ttu-id="2309d-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span><span class="sxs-lookup"><span data-stu-id="2309d-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="2309d-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="2309d-126">SkipWhile</span></span>  
 <span data-ttu-id="2309d-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span><span class="sxs-lookup"><span data-stu-id="2309d-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="2309d-128">The remaining strings in the array are returned.</span><span class="sxs-lookup"><span data-stu-id="2309d-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="2309d-129">Take</span><span class="sxs-lookup"><span data-stu-id="2309d-129">Take</span></span>  
 <span data-ttu-id="2309d-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span><span class="sxs-lookup"><span data-stu-id="2309d-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="2309d-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="2309d-131">TakeWhile</span></span>  
 <span data-ttu-id="2309d-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span><span class="sxs-lookup"><span data-stu-id="2309d-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2309d-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="2309d-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="2309d-134">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2309d-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2309d-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="2309d-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="2309d-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="2309d-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="2309d-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="2309d-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="2309d-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="2309d-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
