---
title: Timer 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 4b0b9a8d57eae774a62c7807bfa071508bb78c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660952"
---
# <a name="timer-component-overview-windows-forms"></a>Timer 组件概述（Windows 窗体）
Windows 窗体 <xref:System.Windows.Forms.Timer> 是一种按固定事件间隔引发事件的组件。 此组件专为 Windows 窗体环境设计。 如果需要适合服务器环境的计时器，请参阅[基于服务器的计时器介绍](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## <a name="key-properties-methods-and-events"></a>键属性、 方法和事件  
 由定义的时间间隔长度<xref:System.Windows.Forms.Timer.Interval%2A>属性，其值是以毫秒为单位。 启用了该组件，<xref:System.Windows.Forms.Timer.Tick>引发事件每个时间间隔。 这是将添加要执行的代码的位置。 有关详细信息，请参阅[如何：使用 Windows 窗体 Timer 组件的设定间隔运行过程](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。 主要方法<xref:System.Windows.Forms.Timer>组件都<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，这将打开和关闭计时器。 关闭计时器时，它将重置;没有方法来暂停<xref:System.Windows.Forms.Timer>组件。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.Timer>
- [Timer 组件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)
- [Windows 窗体 Timer 组件的 Interval 属性的限制](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
