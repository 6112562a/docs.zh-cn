---
title: Handles 子句
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2fecad919722f3da25c48f133a9c92b5e683d5e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345912"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="df6ae-102">Handles 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df6ae-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="df6ae-103">声明某一过程可处理指定的事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df6ae-104">语法</span><span class="sxs-lookup"><span data-stu-id="df6ae-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="df6ae-105">部件</span><span class="sxs-lookup"><span data-stu-id="df6ae-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="df6ae-106">将处理事件的过程的 `Sub` 过程声明。</span><span class="sxs-lookup"><span data-stu-id="df6ae-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="df6ae-107">`proceduredeclaration` 要处理的事件的列表，以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="df6ae-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="df6ae-108">事件必须由当前类的基类引发，或由使用 `WithEvents` 关键字声明的对象引发。</span><span class="sxs-lookup"><span data-stu-id="df6ae-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df6ae-109">备注</span><span class="sxs-lookup"><span data-stu-id="df6ae-109">Remarks</span></span>  
 <span data-ttu-id="df6ae-110">在过程声明的结尾使用 `Handles` 关键字，以使其处理由使用 `WithEvents` 关键字声明的对象变量引发的事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="df6ae-111">`Handles` 关键字还可在派生类中用于处理来自基类的事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="df6ae-112">`Handles` 关键字和 `AddHandler` 语句都允许你指定特定过程处理特定事件，但存在差异。</span><span class="sxs-lookup"><span data-stu-id="df6ae-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="df6ae-113">定义过程时使用 `Handles` 关键字，以指定它处理特定事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="df6ae-114">`AddHandler` 语句在运行时将过程连接到事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="df6ae-115">有关详细信息，请参阅[AddHandler 语句](../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="df6ae-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="df6ae-116">对于自定义事件，应用程序会在添加过程作为事件处理程序时，调用事件的 `AddHandler` 访问器。</span><span class="sxs-lookup"><span data-stu-id="df6ae-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="df6ae-117">有关自定义事件的详细信息，请参阅[Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="df6ae-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df6ae-118">示例</span><span class="sxs-lookup"><span data-stu-id="df6ae-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="df6ae-119">下面的示例演示派生类可以如何使用 `Handles` 语句处理来自基类的事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="df6ae-120">示例</span><span class="sxs-lookup"><span data-stu-id="df6ae-120">Example</span></span>  
 <span data-ttu-id="df6ae-121">下面的示例包含**WPF 应用程序**项目的两个按钮事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="df6ae-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="df6ae-122">示例</span><span class="sxs-lookup"><span data-stu-id="df6ae-122">Example</span></span>  
 <span data-ttu-id="df6ae-123">下面的示例与前面的示例等效。</span><span class="sxs-lookup"><span data-stu-id="df6ae-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="df6ae-124">`eventlist` 子句中的 `Handles` 包含两个按钮的事件。</span><span class="sxs-lookup"><span data-stu-id="df6ae-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="df6ae-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df6ae-125">See also</span></span>

- [<span data-ttu-id="df6ae-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="df6ae-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="df6ae-127">AddHandler 语句</span><span class="sxs-lookup"><span data-stu-id="df6ae-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="df6ae-128">RemoveHandler 语句</span><span class="sxs-lookup"><span data-stu-id="df6ae-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="df6ae-129">Event 语句</span><span class="sxs-lookup"><span data-stu-id="df6ae-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="df6ae-130">RaiseEvent 语句</span><span class="sxs-lookup"><span data-stu-id="df6ae-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="df6ae-131">事件</span><span class="sxs-lookup"><span data-stu-id="df6ae-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
