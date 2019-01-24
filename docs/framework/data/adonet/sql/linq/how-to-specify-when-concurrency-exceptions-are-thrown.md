---
title: 如何：指定引发时并发异常
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: a6a9fa61685caffb7b2b5d1baf9640cb5ccfa31b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587159"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="d443c-102">如何：指定引发时并发异常</span><span class="sxs-lookup"><span data-stu-id="d443c-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="d443c-103">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，当因出现开放式并发冲突而导致对象不能更新时，会引发 <xref:System.Data.Linq.ChangeConflictException> 异常。</span><span class="sxs-lookup"><span data-stu-id="d443c-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="d443c-104">有关详细信息，请参阅[开放式并发：概述](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d443c-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="d443c-105">在向数据库提交您所做的更改前，您可以指定应何时引发并发异常：</span><span class="sxs-lookup"><span data-stu-id="d443c-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="d443c-106">第一次失败时引发异常 (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>)。</span><span class="sxs-lookup"><span data-stu-id="d443c-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="d443c-107">完成所有更新尝试，积累所有失败，然后在异常中报告积累的失败 (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>)。</span><span class="sxs-lookup"><span data-stu-id="d443c-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="d443c-108">引发 <xref:System.Data.Linq.ChangeConflictException> 异常时，该异常会提供对 <xref:System.Data.Linq.ChangeConflictCollection> 集合的访问。</span><span class="sxs-lookup"><span data-stu-id="d443c-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="d443c-109">此集合提供了有关每个冲突（映射到单个失败的更新尝试）的详细信息，包括对 <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> 集合的访问。</span><span class="sxs-lookup"><span data-stu-id="d443c-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="d443c-110">每个成员冲突映射到未通过并发检查的更新中的单个成员。</span><span class="sxs-lookup"><span data-stu-id="d443c-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d443c-111">示例</span><span class="sxs-lookup"><span data-stu-id="d443c-111">Example</span></span>  
 <span data-ttu-id="d443c-112">下面的代码显示了这两个值的示例。</span><span class="sxs-lookup"><span data-stu-id="d443c-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d443c-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="d443c-113">See also</span></span>
- [<span data-ttu-id="d443c-114">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="d443c-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d443c-115">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="d443c-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
