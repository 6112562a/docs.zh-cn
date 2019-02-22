---
title: 在 Windows 窗体中创建事件处理程序
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: c77a004d52afc67a3811ff98e9a62c788c001803
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664778"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="0be5e-102">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="0be5e-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="0be5e-103">事件处理程序是代码中的过程，用于确定事件（例如用户单击按钮或消息队列收到消息）发生时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0be5e-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="0be5e-104">引发事件时，将执行收到该事件的一个或多个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0be5e-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="0be5e-105">可以将事件分配给多个处理程序，并且可以动态更改处理特定事件的方法。</span><span class="sxs-lookup"><span data-stu-id="0be5e-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="0be5e-106">还可以使用 Windows 窗体设计器来创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0be5e-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0be5e-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="0be5e-107">In This Section</span></span>  
 [<span data-ttu-id="0be5e-108">事件概述</span><span class="sxs-lookup"><span data-stu-id="0be5e-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="0be5e-109">解释事件模型和委托的角色。</span><span class="sxs-lookup"><span data-stu-id="0be5e-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="0be5e-110">事件处理程序概述</span><span class="sxs-lookup"><span data-stu-id="0be5e-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="0be5e-111">描述如何处理事件。</span><span class="sxs-lookup"><span data-stu-id="0be5e-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="0be5e-112">如何：在运行时为 Windows 窗体创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="0be5e-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="0be5e-113">提供有关如何动态响应系统或用户事件的指令。</span><span class="sxs-lookup"><span data-stu-id="0be5e-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="0be5e-114">如何：将多个事件连接到 Windows 窗体中的单个事件处理程序</span><span class="sxs-lookup"><span data-stu-id="0be5e-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="0be5e-115">提供有关通过事件将同一功能分配给多个控件的指令。</span><span class="sxs-lookup"><span data-stu-id="0be5e-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="0be5e-116">Windows 窗体中的事件顺序</span><span class="sxs-lookup"><span data-stu-id="0be5e-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="0be5e-117">描述在 Windows 窗体控件中引发事件的顺序。</span><span class="sxs-lookup"><span data-stu-id="0be5e-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 <span data-ttu-id="0be5e-118">[如何：创建事件处理程序使用设计器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0be5e-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span></span>  
 <span data-ttu-id="0be5e-119">描述如何使用 Windows 窗体设计器来创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0be5e-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0be5e-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="0be5e-120">Related Sections</span></span>  
 [<span data-ttu-id="0be5e-121">事件</span><span class="sxs-lookup"><span data-stu-id="0be5e-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="0be5e-122">提供一些指向有关使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 处理和引发事件的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="0be5e-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="0be5e-123">Visual Basic 中继承的事件处理程序疑难解答</span><span class="sxs-lookup"><span data-stu-id="0be5e-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="0be5e-124">列出了继承的组件中的事件处理程序所发生的常见问题。</span><span class="sxs-lookup"><span data-stu-id="0be5e-124">Lists common issues that occur with event handlers in inherited components.</span></span>
