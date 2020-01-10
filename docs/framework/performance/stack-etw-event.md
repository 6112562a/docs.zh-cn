---
title: 堆栈 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: f3014a04ba7cacbe37b6706e2919ffd7de19aa65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715911"
---
# <a name="stack-etw-event"></a><span data-ttu-id="e7fc4-102">堆栈 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e7fc4-102">Stack ETW Event</span></span>
<span data-ttu-id="e7fc4-103">堆栈事件应与其他事件结合使用，在引发事件后生成堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="e7fc4-104">启用运行时提供程序时，记录该事件。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="e7fc4-105">这是一个发生频率非常高的事件，因为每当引发另一个运行时事件时，都将引发此事件。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="e7fc4-106">因此，我们建议谨慎使用此事件。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="e7fc4-107">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="e7fc4-108">（有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）</span><span class="sxs-lookup"><span data-stu-id="e7fc4-108">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e7fc4-109">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e7fc4-109">Keyword for raising the event</span></span>|<span data-ttu-id="e7fc4-110">Level</span><span class="sxs-lookup"><span data-stu-id="e7fc4-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e7fc4-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="e7fc4-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="e7fc4-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="e7fc4-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="e7fc4-113">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e7fc4-114">Event</span><span class="sxs-lookup"><span data-stu-id="e7fc4-114">Event</span></span>|<span data-ttu-id="e7fc4-115">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e7fc4-115">Event ID</span></span>|<span data-ttu-id="e7fc4-116">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e7fc4-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="e7fc4-117">82</span><span class="sxs-lookup"><span data-stu-id="e7fc4-117">82</span></span>|<span data-ttu-id="e7fc4-118">与其他事件结合使用，在事件发生后生成堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="e7fc4-119">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e7fc4-120">字段名</span><span class="sxs-lookup"><span data-stu-id="e7fc4-120">Field name</span></span>|<span data-ttu-id="e7fc4-121">数据类型</span><span class="sxs-lookup"><span data-stu-id="e7fc4-121">Data Type</span></span>|<span data-ttu-id="e7fc4-122">描述</span><span class="sxs-lookup"><span data-stu-id="e7fc4-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e7fc4-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e7fc4-123">ClrInstanceID</span></span>|<span data-ttu-id="e7fc4-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="e7fc4-124">win:Uint16</span></span>|<span data-ttu-id="e7fc4-125">唯一运行时标识符。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="e7fc4-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="e7fc4-126">Reserved1</span></span>|<span data-ttu-id="e7fc4-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="e7fc4-127">win:UInt8</span></span>|<span data-ttu-id="e7fc4-128">保留。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-128">Reserved.</span></span>|  
|<span data-ttu-id="e7fc4-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="e7fc4-129">Reserved2</span></span>|<span data-ttu-id="e7fc4-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="e7fc4-130">win:UInt8</span></span>|<span data-ttu-id="e7fc4-131">保留。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-131">Reserved.</span></span>|  
|<span data-ttu-id="e7fc4-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="e7fc4-132">FrameCount</span></span>|<span data-ttu-id="e7fc4-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7fc4-133">win:UInt32</span></span>|<span data-ttu-id="e7fc4-134">堆栈跟踪中的帧数。</span><span class="sxs-lookup"><span data-stu-id="e7fc4-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="e7fc4-135">堆栈</span><span class="sxs-lookup"><span data-stu-id="e7fc4-135">Stack</span></span>|<span data-ttu-id="e7fc4-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="e7fc4-136">win:Pointer</span></span>|<span data-ttu-id="e7fc4-137">指令指针的列</span><span class="sxs-lookup"><span data-stu-id="e7fc4-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7fc4-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7fc4-138">See also</span></span>

- [<span data-ttu-id="e7fc4-139">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e7fc4-139">CLR ETW Events</span></span>](clr-etw-events.md)
