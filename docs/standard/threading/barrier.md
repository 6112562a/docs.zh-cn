---
title: 屏障
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 081a4e66462ab546bf4738b4a8b06a4a2ec91a1d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645024"
---
# <a name="barrier"></a><span data-ttu-id="81a62-102">屏障</span><span class="sxs-lookup"><span data-stu-id="81a62-102">Barrier</span></span>

<span data-ttu-id="81a62-103"><xref:System.Threading.Barrier?displayProperty=nameWithType> 是同步基元，可以使多个线程（称为“参与者”）分阶段同时处理算法。</span><span class="sxs-lookup"><span data-stu-id="81a62-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="81a62-104">达到代码中的屏障点之前，每个参与者将继续执行。</span><span class="sxs-lookup"><span data-stu-id="81a62-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="81a62-105">屏障表示工作阶段的末尾。</span><span class="sxs-lookup"><span data-stu-id="81a62-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="81a62-106">单个参与者到达屏障后将被阻止，直至所有参与者都已达到同一障碍。</span><span class="sxs-lookup"><span data-stu-id="81a62-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="81a62-107">所有参与者都已达到屏障后，你可以选择调用阶段后操作。</span><span class="sxs-lookup"><span data-stu-id="81a62-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="81a62-108">此阶段后操作可由单线程用于执行操作，而所有其他线程仍被阻止。</span><span class="sxs-lookup"><span data-stu-id="81a62-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="81a62-109">执行此操作后，所有参与者将不受阻止。</span><span class="sxs-lookup"><span data-stu-id="81a62-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="81a62-110">以下代码片段演示了基本屏障模式。</span><span class="sxs-lookup"><span data-stu-id="81a62-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="81a62-111">有关完整示例，请参阅[如何：使用屏障同步并发操作](how-to-synchronize-concurrent-operations-with-a-barrier.md)。</span><span class="sxs-lookup"><span data-stu-id="81a62-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="81a62-112">添加和删除参与者</span><span class="sxs-lookup"><span data-stu-id="81a62-112">Adding and removing participants</span></span>

 <span data-ttu-id="81a62-113">创建 <xref:System.Threading.Barrier> 实例时，需指定参与者数量。</span><span class="sxs-lookup"><span data-stu-id="81a62-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="81a62-114">还可以随时动态添加或删除参与者。</span><span class="sxs-lookup"><span data-stu-id="81a62-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="81a62-115">例如，如果其中一个参与者解决了问题的一部分，可以存储结果，停止执行相应线程，并调用 <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> 以减少屏障中的参与者数量。</span><span class="sxs-lookup"><span data-stu-id="81a62-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="81a62-116">当通过调用 <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType> 添加参与者时，返回值将指定当前阶段的数量，这在初始化新的参与者的工作时很有用。</span><span class="sxs-lookup"><span data-stu-id="81a62-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="81a62-117">断开的屏障</span><span class="sxs-lookup"><span data-stu-id="81a62-117">Broken barriers</span></span>

 <span data-ttu-id="81a62-118">如果一个参与者无法到达屏障，则可能发生死锁。</span><span class="sxs-lookup"><span data-stu-id="81a62-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="81a62-119">若要避免这些死锁，请使用 <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> 方法的重载来指定超时期限和取消标记。</span><span class="sxs-lookup"><span data-stu-id="81a62-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="81a62-120">这些重载将返回一个布尔值，每个参与者均可在继续到下一阶段前进行检查。</span><span class="sxs-lookup"><span data-stu-id="81a62-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="81a62-121">阶段后异常</span><span class="sxs-lookup"><span data-stu-id="81a62-121">Post-phase exceptions</span></span>

 <span data-ttu-id="81a62-122">如果阶段后委托引发异常，则它将包装在 <xref:System.Threading.BarrierPostPhaseException> 对象中，然后传播到所有参与者。</span><span class="sxs-lookup"><span data-stu-id="81a62-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="81a62-123">屏障与 ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="81a62-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="81a62-124">当线程执行循环中的多个阶段时，屏障特别有用。</span><span class="sxs-lookup"><span data-stu-id="81a62-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="81a62-125">如果你的代码仅需一个或多个工作阶段，则应考虑是否配合使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 对象与任何类型的隐式联接，其中包括：</span><span class="sxs-lookup"><span data-stu-id="81a62-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="81a62-126">有关详细信息，请参阅[使用延续任务链接任务](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="81a62-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a62-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="81a62-127">See also</span></span>

- [<span data-ttu-id="81a62-128">线程处理对象和功能</span><span class="sxs-lookup"><span data-stu-id="81a62-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="81a62-129">如何：使用屏障同步并发操作</span><span class="sxs-lookup"><span data-stu-id="81a62-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
