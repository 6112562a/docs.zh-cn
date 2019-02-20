---
title: 处理用户输入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: 8c6319929d4b419cc0a2e1cfd097bfae7d997120
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442994"
---
# <a name="handling-user-input"></a><span data-ttu-id="97f26-102">处理用户输入</span><span class="sxs-lookup"><span data-stu-id="97f26-102">Handling User Input</span></span>
<span data-ttu-id="97f26-103">本主题介绍了提供的主键盘和鼠标事件<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="97f26-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97f26-104">处理事件时，控件作者应重写受保护的 `On`*EventName* 方法，而不是向事件附加委托。</span><span class="sxs-lookup"><span data-stu-id="97f26-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="97f26-105">若要查看事件，请参阅[从组件引发事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="97f26-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97f26-106">如果没有与事件的基类的实例相关联的数据<xref:System.EventArgs>作为参数传递`On` *EventName*方法。</span><span class="sxs-lookup"><span data-stu-id="97f26-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="97f26-107">键盘事件</span><span class="sxs-lookup"><span data-stu-id="97f26-107">Keyboard Events</span></span>  
 <span data-ttu-id="97f26-108">控件可处理的常见键盘事件包括<xref:System.Windows.Forms.Control.KeyDown>， <xref:System.Windows.Forms.Control.KeyPress>，和<xref:System.Windows.Forms.Control.KeyUp>。</span><span class="sxs-lookup"><span data-stu-id="97f26-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="97f26-109">事件名称</span><span class="sxs-lookup"><span data-stu-id="97f26-109">Event Name</span></span>|<span data-ttu-id="97f26-110">要重写的方法</span><span class="sxs-lookup"><span data-stu-id="97f26-110">Method to Override</span></span>|<span data-ttu-id="97f26-111">事件说明</span><span class="sxs-lookup"><span data-stu-id="97f26-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="97f26-112">仅在最初按下键时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="97f26-113">每次按键时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="97f26-114">如果按住某个键，<xref:System.Windows.Forms.Control.KeyPress>由操作系统定义的重复速率引发事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="97f26-115">在松开某个键时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="97f26-116">处理键盘输入比重写上表中的事件要复杂得多，这超出了本主题的讨论范围。</span><span class="sxs-lookup"><span data-stu-id="97f26-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="97f26-117">有关详细信息，请参阅 [Windows 窗体中的用户输入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="97f26-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="97f26-118">鼠标事件</span><span class="sxs-lookup"><span data-stu-id="97f26-118">Mouse Events</span></span>  
 <span data-ttu-id="97f26-119">控件可处理的鼠标事件都<xref:System.Windows.Forms.Control.MouseDown>， <xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseHover>， <xref:System.Windows.Forms.Control.MouseLeave>， <xref:System.Windows.Forms.Control.MouseMove>，并<xref:System.Windows.Forms.Control.MouseUp>。</span><span class="sxs-lookup"><span data-stu-id="97f26-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="97f26-120">事件名称</span><span class="sxs-lookup"><span data-stu-id="97f26-120">Event Name</span></span>|<span data-ttu-id="97f26-121">要重写的方法</span><span class="sxs-lookup"><span data-stu-id="97f26-121">Method to Override</span></span>|<span data-ttu-id="97f26-122">事件说明</span><span class="sxs-lookup"><span data-stu-id="97f26-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="97f26-123">指针位于控件上时，按下鼠标按钮会引发该事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="97f26-124">指针首次进入控件区域时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="97f26-125">指针悬停在控件上时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="97f26-126">指针离开控件区域时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="97f26-127">指针在控件区域中移动时引发。</span><span class="sxs-lookup"><span data-stu-id="97f26-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="97f26-128">指针位于控件上或指针离开控件区域时，松开鼠标按钮会引发该事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="97f26-129">下面的代码段显示的重写示例<xref:System.Windows.Forms.Control.MouseDown>事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="97f26-130">下面的代码段显示的重写示例<xref:System.Windows.Forms.Control.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="97f26-131">下面的代码段显示的重写示例<xref:System.Windows.Forms.Control.MouseUp>事件。</span><span class="sxs-lookup"><span data-stu-id="97f26-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="97f26-132">有关完整的源代码`FlashTrackBar`示例，请参阅[如何：创建显示进度的 Windows 窗体控件](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="97f26-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f26-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="97f26-133">See also</span></span>
- [<span data-ttu-id="97f26-134">Windows 窗体控件中的事件</span><span class="sxs-lookup"><span data-stu-id="97f26-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [<span data-ttu-id="97f26-135">定义事件</span><span class="sxs-lookup"><span data-stu-id="97f26-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="97f26-136">事件</span><span class="sxs-lookup"><span data-stu-id="97f26-136">Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="97f26-137">Windows 窗体中的用户输入</span><span class="sxs-lookup"><span data-stu-id="97f26-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
