---
title: 如何：设置绑定更新的通知
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: ca6af88d6ba8ba4e242faa5d1443ee95925fbe2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511860"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="a3a8a-102">如何：设置绑定更新的通知</span><span class="sxs-lookup"><span data-stu-id="a3a8a-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="a3a8a-103">本示例演示如何设置在绑定的绑定目标（目标）或绑定源（源）属性更新时收到通知。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a8a-104">示例</span><span class="sxs-lookup"><span data-stu-id="a3a8a-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="a3a8a-105">在每次更新绑定源或目标时都会引发数据更新事件。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="a3a8a-106">从内部来看，此事件用于通知用户界面 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 执行更新，因为绑定数据已更改。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="a3a8a-107">注意，要确保这些事件起作用，并确保单向或双向绑定正常工作，需要使用 <xref:System.ComponentModel.INotifyPropertyChanged> 接口实现数据类。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="a3a8a-108">有关详细信息，请参阅[实现属性更改通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-108">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="a3a8a-109">将绑定中的 <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> 或 <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> 属性（或两者）设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="a3a8a-110">提供的用于侦听此事件的处理程序必须直接附加到希望收到更改通知的元素，但如果希望在上下文中的任何内容发生变化时得到通知，则必须附加到整个数据上下文。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="a3a8a-111">下面的示例演示如何设置当目标属性更新时收到通知。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="a3a8a-112">然后，可以根据 EventHandler\<T> 委托（在本示例中为 *OnTargetUpdated*）分配处理程序来处理该事件：</span><span class="sxs-lookup"><span data-stu-id="a3a8a-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="a3a8a-113">事件的参数可用于确定已更改属性的详细信息（例如，如果同一处理程序附加到多个元素，则可确定类型或特定元素信息），如果在单个元素上有多个绑定属性，则这些详细信息将很有用。</span><span class="sxs-lookup"><span data-stu-id="a3a8a-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a8a-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="a3a8a-114">See also</span></span>
- [<span data-ttu-id="a3a8a-115">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="a3a8a-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a3a8a-116">帮助主题</span><span class="sxs-lookup"><span data-stu-id="a3a8a-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
