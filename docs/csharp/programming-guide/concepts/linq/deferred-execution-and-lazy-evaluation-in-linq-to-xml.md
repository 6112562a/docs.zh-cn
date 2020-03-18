---
title: LINQ to XML 中的延迟执行和迟缓计算 (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594564"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="37bd3-102">LINQ to XML 中的延迟执行和迟缓计算 (C#)</span><span class="sxs-lookup"><span data-stu-id="37bd3-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="37bd3-103">实现查询和轴操作通常是为了使用延迟执行。</span><span class="sxs-lookup"><span data-stu-id="37bd3-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="37bd3-104">本主题解释延迟执行的要求和优点，以及某些实现注意事项。</span><span class="sxs-lookup"><span data-stu-id="37bd3-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="37bd3-105">延迟执行</span><span class="sxs-lookup"><span data-stu-id="37bd3-105">Deferred Execution</span></span>  
 <span data-ttu-id="37bd3-106">延迟执行意味着表达式的计算延迟，直到真正需要其实现  值为止。</span><span class="sxs-lookup"><span data-stu-id="37bd3-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="37bd3-107">当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。</span><span class="sxs-lookup"><span data-stu-id="37bd3-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="37bd3-108">在最佳情况下，延迟执行只允许对源集合的单个循环访问。</span><span class="sxs-lookup"><span data-stu-id="37bd3-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="37bd3-109">LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。</span><span class="sxs-lookup"><span data-stu-id="37bd3-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="37bd3-110">在迭代器块内使用时，C# 语言可以通过 [yield](../../../language-reference/keywords/yield.md) 关键字（以 `yield-return` 语句形式），直接支持延迟执行。</span><span class="sxs-lookup"><span data-stu-id="37bd3-110">Deferred execution is supported directly in the C# language by the [yield](../../../language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="37bd3-111">此类迭代器必须返回类型为 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>（或派生类型）的集合。</span><span class="sxs-lookup"><span data-stu-id="37bd3-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="37bd3-112">积极与迟缓计算</span><span class="sxs-lookup"><span data-stu-id="37bd3-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="37bd3-113">当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。</span><span class="sxs-lookup"><span data-stu-id="37bd3-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
- <span data-ttu-id="37bd3-114">在迟缓计算  中，每次调用迭代器时都会处理源集合的一个元素。</span><span class="sxs-lookup"><span data-stu-id="37bd3-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="37bd3-115">这是实现迭代器的典型方式。</span><span class="sxs-lookup"><span data-stu-id="37bd3-115">This is the typical way in which iterators are implemented.</span></span>  
  
- <span data-ttu-id="37bd3-116">在积极计算  中，第一次调用迭代器时就会对整个集合进行处理。</span><span class="sxs-lookup"><span data-stu-id="37bd3-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="37bd3-117">还可能需要源集合的临时副本。</span><span class="sxs-lookup"><span data-stu-id="37bd3-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="37bd3-118">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。</span><span class="sxs-lookup"><span data-stu-id="37bd3-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="37bd3-119">迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。</span><span class="sxs-lookup"><span data-stu-id="37bd3-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="37bd3-120">当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。</span><span class="sxs-lookup"><span data-stu-id="37bd3-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="37bd3-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="37bd3-121">Next Steps</span></span>  
 <span data-ttu-id="37bd3-122">本教程的下一个主题将解释延迟执行：</span><span class="sxs-lookup"><span data-stu-id="37bd3-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
- [<span data-ttu-id="37bd3-123">延迟执行示例 (C#)</span><span class="sxs-lookup"><span data-stu-id="37bd3-123">Deferred Execution Example (C#)</span></span>](./deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="37bd3-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37bd3-124">See also</span></span>

- [<span data-ttu-id="37bd3-125">教程：将查询链接在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="37bd3-125">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [<span data-ttu-id="37bd3-126">概念和术语（功能转换）(C#)</span><span class="sxs-lookup"><span data-stu-id="37bd3-126">Concepts and Terminology (Functional Transformation) (C#)</span></span>](./concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="37bd3-127">聚合运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="37bd3-127">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)
- [<span data-ttu-id="37bd3-128">yield</span><span class="sxs-lookup"><span data-stu-id="37bd3-128">yield</span></span>](../../../language-reference/keywords/yield.md)
