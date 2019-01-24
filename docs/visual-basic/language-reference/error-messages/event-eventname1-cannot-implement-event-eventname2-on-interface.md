---
title: 事件&#39; &lt;eventname1&gt; &#39;不能实现事件&#39; &lt;eventname2&gt; &#39;接口上&#39;&lt;接口&gt;&#39;因为它们的委托类型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不匹配
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638205"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="f3965-102">事件&#39; &lt;eventname1&gt; &#39;不能实现事件&#39; &lt;eventname2&gt; &#39;接口上&#39;&lt;接口&gt;&#39;因为它们的委托类型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不匹配</span><span class="sxs-lookup"><span data-stu-id="f3965-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="f3965-103">Visual Basic 不能实现某个事件，因为该事件的委托类型与该接口中的事件的委托类型不匹配。</span><span class="sxs-lookup"><span data-stu-id="f3965-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="f3965-104">如果在接口中定义了多个事件，然后试图用一个事件同时实现这些事件，则可能发生此错误。</span><span class="sxs-lookup"><span data-stu-id="f3965-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="f3965-105">只有当所有要实现的事件都使用 `As` 语法进行声明并指定相同的委托类型时，事件才能实现两个或更多个事件。</span><span class="sxs-lookup"><span data-stu-id="f3965-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="f3965-106">**错误 ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="f3965-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3965-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f3965-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f3965-108">单独实现事件。</span><span class="sxs-lookup"><span data-stu-id="f3965-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="f3965-109">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f3965-109">—or—</span></span>  
  
-   <span data-ttu-id="f3965-110">使用在接口中定义的事件`As`语法，并指定相同的委托类型。</span><span class="sxs-lookup"><span data-stu-id="f3965-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3965-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3965-111">See also</span></span>
- [<span data-ttu-id="f3965-112">Event 语句</span><span class="sxs-lookup"><span data-stu-id="f3965-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="f3965-113">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="f3965-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f3965-114">事件</span><span class="sxs-lookup"><span data-stu-id="f3965-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
