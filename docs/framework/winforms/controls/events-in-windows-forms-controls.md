---
title: Windows 窗体控件中的事件
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 56de08f039fd4dee9dcc5a1b3f86cc0e8e577b43
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442433"
---
# <a name="events-in-windows-forms-controls"></a>Windows 窗体控件中的事件
Windows 窗体控件继承六十多个事件从<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 其中包括<xref:System.Windows.Forms.Control.Paint>事件，这会导致要绘制的控件、 事件与显示一个窗口，如相关<xref:System.Windows.Forms.Control.Resize>和<xref:System.Windows.Forms.Control.Layout>事件和低级别的鼠标和键盘事件。 某些低级别事件通过合成<xref:System.Windows.Forms.Control>到语义事件，如<xref:System.Windows.Forms.Control.Click>和<xref:System.Windows.Forms.Control.DoubleClick>。 有关继承事件的详细信息，请参阅<xref:System.Windows.Forms.Control>。  
  
 如果自定义控件需要重写继承事件功能，请重写继承的 `On`*EventName* 方法，而不附加委托。 如果不熟悉 .NET Framework 中的事件模型，请参阅[从组件引发事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。  
  
## <a name="see-also"></a>请参阅
- [重写 OnPaint 方法](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [处理用户输入](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [定义事件](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [事件](../../../../docs/standard/events/index.md)
