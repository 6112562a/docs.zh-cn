---
title: Timer 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 5bef0ba87d6a496acf7575965128be2b20b437ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074204"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="b63ae-102">Timer 组件概述（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="b63ae-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b63ae-103">Windows 窗体 <xref:System.Windows.Forms.Timer> 是一种按固定事件间隔引发事件的组件。</span><span class="sxs-lookup"><span data-stu-id="b63ae-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="b63ae-104">此组件专为 Windows 窗体环境设计。</span><span class="sxs-lookup"><span data-stu-id="b63ae-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b63ae-105">如果需要适合服务器环境的计时器，请参阅[基于服务器的计时器介绍](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="b63ae-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="b63ae-106">键属性、 方法和事件</span><span class="sxs-lookup"><span data-stu-id="b63ae-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="b63ae-107">由定义的时间间隔长度<xref:System.Windows.Forms.Timer.Interval%2A>属性，其值是以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="b63ae-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="b63ae-108">启用了该组件，<xref:System.Windows.Forms.Timer.Tick>引发事件每个时间间隔。</span><span class="sxs-lookup"><span data-stu-id="b63ae-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="b63ae-109">这是将添加要执行的代码的位置。</span><span class="sxs-lookup"><span data-stu-id="b63ae-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="b63ae-110">有关详细信息，请参阅[如何：使用 Windows 窗体 Timer 组件的设定间隔运行过程](run-procedures-at-set-intervals-with-wf-timer-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b63ae-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="b63ae-111">主要方法<xref:System.Windows.Forms.Timer>组件都<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，这将打开和关闭计时器。</span><span class="sxs-lookup"><span data-stu-id="b63ae-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="b63ae-112">关闭计时器时，它将重置;没有方法来暂停<xref:System.Windows.Forms.Timer>组件。</span><span class="sxs-lookup"><span data-stu-id="b63ae-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63ae-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="b63ae-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="b63ae-114">Timer 组件</span><span class="sxs-lookup"><span data-stu-id="b63ae-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="b63ae-115">Windows 窗体 Timer 组件的 Interval 属性的限制</span><span class="sxs-lookup"><span data-stu-id="b63ae-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
