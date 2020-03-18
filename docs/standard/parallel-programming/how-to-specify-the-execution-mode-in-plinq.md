---
title: 如何：在 PLINQ 中指定执行模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: c602aba6e18f80b007b15cd61dfd2b48a36dd2c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139244"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="595c3-102">如何：在 PLINQ 中指定执行模式</span><span class="sxs-lookup"><span data-stu-id="595c3-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="595c3-103">此示例展示了如何强制 PLINQ 规避默认启发，同时并行执行查询，无论查询的形状如何。</span><span class="sxs-lookup"><span data-stu-id="595c3-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="595c3-104">本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。</span><span class="sxs-lookup"><span data-stu-id="595c3-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="595c3-105">若要详细了解加速，请参阅[了解 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="595c3-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="595c3-106">示例</span><span class="sxs-lookup"><span data-stu-id="595c3-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="595c3-107">PLINQ 旨在利用机会并行执行查询。</span><span class="sxs-lookup"><span data-stu-id="595c3-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="595c3-108">不过，并非所有查询都受益于并行执行。</span><span class="sxs-lookup"><span data-stu-id="595c3-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="595c3-109">例如，如果查询包含一个工作量极小的用户委托，顺序运行查询的速度通常更快。</span><span class="sxs-lookup"><span data-stu-id="595c3-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="595c3-110">这是因为相较所实现的加速，启用并行执行所涉及的开销更加昂贵。</span><span class="sxs-lookup"><span data-stu-id="595c3-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="595c3-111">因此，PLINQ 并不自动并行执行每个查询。</span><span class="sxs-lookup"><span data-stu-id="595c3-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="595c3-112">它先检查查询的形状和所包含的各种运算符。</span><span class="sxs-lookup"><span data-stu-id="595c3-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="595c3-113">根据此分析，默认执行模式下的 PLINQ 可能会决定顺序执行部分或全部查询。</span><span class="sxs-lookup"><span data-stu-id="595c3-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="595c3-114">不过，在某些情况下，你对查询更加了解，所做决定可能优于 PLINQ 根据分析所做的决定。</span><span class="sxs-lookup"><span data-stu-id="595c3-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="595c3-115">例如，你可能知道委托非常昂贵，且查询一定会受益于并行执行。</span><span class="sxs-lookup"><span data-stu-id="595c3-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="595c3-116">在这种情况下，可以使用 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> 方法并指定 <xref:System.Linq.ParallelExecutionMode.ForceParallelism> 值，以指示 PLINQ 始终并行运行查询。</span><span class="sxs-lookup"><span data-stu-id="595c3-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="595c3-117">编译代码</span><span class="sxs-lookup"><span data-stu-id="595c3-117">Compiling the Code</span></span>  
 <span data-ttu-id="595c3-118">将此代码剪切并粘贴到 [PLINQ 数据样本](../../../docs/standard/parallel-programming/plinq-data-sample.md)中，并通过 `Main` 调用方法。</span><span class="sxs-lookup"><span data-stu-id="595c3-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595c3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="595c3-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="595c3-120">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="595c3-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
