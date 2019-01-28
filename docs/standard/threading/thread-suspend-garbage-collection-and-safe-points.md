---
title: Thread.Suspend、垃圾回收和安全点
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3e44b81b519bcae42c2e69eff46e73b1ae631a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490799"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="285cf-102">Thread.Suspend、垃圾回收和安全点</span><span class="sxs-lookup"><span data-stu-id="285cf-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="285cf-103">如果对线程调用 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>，系统就会注意到线程暂停请求已发出，并允许线程在实际暂停前一直执行到安全点。</span><span class="sxs-lookup"><span data-stu-id="285cf-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="285cf-104">线程的安全点是可以执行垃圾回收的执行点。</span><span class="sxs-lookup"><span data-stu-id="285cf-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="285cf-105">一旦达到安全点，运行时就会确保暂停的线程在托管代码中不会进一步取得任何进展。</span><span class="sxs-lookup"><span data-stu-id="285cf-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="285cf-106">在托管代码外部执行的线程始终都可以安全执行垃圾回收，并继续执行到尝试恢复执行托管代码。</span><span class="sxs-lookup"><span data-stu-id="285cf-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="285cf-107">为了执行垃圾回收，运行时必须暂停所有线程（执行回收的线程除外）。</span><span class="sxs-lookup"><span data-stu-id="285cf-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="285cf-108">每个线程必须先到达安全点，然后才能暂停。</span><span class="sxs-lookup"><span data-stu-id="285cf-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285cf-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="285cf-109">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.GC>
- [<span data-ttu-id="285cf-110">线程处理</span><span class="sxs-lookup"><span data-stu-id="285cf-110">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="285cf-111">自动内存管理</span><span class="sxs-lookup"><span data-stu-id="285cf-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
