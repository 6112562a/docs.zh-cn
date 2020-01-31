---
title: 이벤트 개요
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 59085597789d12ce80648efb77859228e4718a3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743483"
---
# <a name="events-overview-windows-forms"></a>이벤트 개요(Windows Forms)
이벤트는 코드에서 응답, 즉 "처리"할 수 있는 작업입니다. 마우스를 클릭하거나 키를 누르는 등의 사용자 작업, 프로그램 코드 또는 시스템에 의해 이벤트가 생성될 수 있습니다.

 이벤트 구동 애플리케이션은 이벤트에 대한 응답으로 코드를 실행합니다. 각 폼과 컨트롤은 미리 정의된 이벤트 집합을 표시하며 이러한 이벤트에 대해 프로그래밍을 수행할 수 있습니다. 이러한 이벤트 중 하나가 발생할 때 연결된 이벤트 처리기에 코드가 있으면 해당 코드가 호출됩니다.

 개체에 의해 발생하는 이벤트 형식은 다양하지만 대부분의 형식은 대다수 컨트롤에 공통적으로 적용됩니다. 예를 들어 대부분의 개체는 <xref:System.Windows.Forms.Control.Click> 이벤트를 처리합니다. 사용자가 폼을 클릭하면 폼의 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기에 포함된 코드가 실행됩니다.

> [!NOTE]
> 대부분의 이벤트는 다른 이벤트와 함께 발생합니다. 예를 들어 <xref:System.Windows.Forms.Control.DoubleClick> 이벤트가 발생하는 과정에서는 <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp> 및 <xref:System.Windows.Forms.Control.Click> 이벤트도 발생합니다.

 有关如何引发和使用事件的信息，请参阅[事件](../../standard/events/index.md)。

## <a name="delegates-and-their-role"></a>대리자 및 해당 역할
 委托是在 .NET Framework 中通常用于生成事件处理机制的类。 委托大致等同于函数指针，通常用于视觉C++对象和其他面向对象的语言。 그러나 함수 포인터와는 달리 대리자는 개체 지향적이고 형식이 안전하며 보안이 유지됩니다. 또한 함수 포인터는 특정 함수에 대한 참조만을 포함하지만 대리자는 개체 참조와 해당 개체 내에 있는 하나 이상의 메서드에 대한 참조로 구성됩니다.

 此事件模型使用*委托*将事件绑定到用于处理这些事件的方法。 대리자는 처리기 메서드를 지정하여 다른 클래스가 이벤트 알림을 등록할 수 있도록 설정합니다. 이벤트가 발생하면 대리자가 bound 메서드를 호출합니다. 有关如何定义委托的详细信息，请参阅[事件](../../standard/events/index.md)。

대리자는 단일 메서드에 바인딩될 수도 있고 여러 메서드에 바인딩(멀티캐스트)될 수도 있습니다. 为事件创建委托时，您（或 Windows）通常会创建多路广播事件。 이때 논리적으로 이벤트당 여러 번 반복되지 않는 특정 절차(예: 대화 상자 표시)를 수행하는 이벤트가 드물지만 예외적으로 발생할 수 있습니다. 有关如何创建多播委托的信息，请参阅[如何合并委托（多路广播委托）](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)。

 멀티캐스트 대리자는 바인딩 대상 메서드의 호출 목록을 유지 관리하며, 호출 목록에 메서드를 추가하기 위한 <xref:System.Delegate.Combine%2A> 메서드와 해당 메서드를 제거하기 위한 <xref:System.Delegate.Remove%2A> 메서드를 지원합니다.

 애플리케이션이 이벤트를 기록하면 컨트롤은 해당 이벤트의 대리자를 호출하여 이벤트를 발생시킵니다. 그러면 대리자는 bound 메서드를 호출합니다. 가장 일반적인 경우(멀티캐스트 대리자)에서 대리자는 호출 목록의 각 bound 메서드를 차례로 호출하므로 일대다 알림이 제공됩니다. 이러한 전략이 사용되므로 컨트롤이 이벤트 알림을 위해 대상 개체 목록을 유지하지 않아도 됩니다. 대리자가 모든 등록과 알림을 처리하기 때문입니다.

 또한 대리자는 여러 이벤트를 같은 메서드에 바인딩할 수 있도록 함으로써 다대일 알림도 허용합니다. 예를 들어 단추 클릭 이벤트와 메뉴 명령 클릭 이벤트 모두가 같은 대리자를 호출할 수 있으며, 이 대리자는 단일 메서드를 호출하여 두 개별 이벤트를 같은 방식으로 처리합니다.

 대리자에는 동적 바인딩 메커니즘이 사용되므로 대리자는 런타임에 서명이 이벤트 처리기의 서명과 일치하는 모든 메서드에 바인딩될 수 있습니다. 이 기능을 사용하면 조건에 따라 bound 메서드를 설정하거나 변경하고 이벤트 처리기를 컨트롤에 동적으로 연결할 수 있습니다.

## <a name="see-also"></a>另请参阅

- [Windows Forms에서 이벤트 처리기 만들기](creating-event-handlers-in-windows-forms.md)
- [이벤트 처리기 개요](event-handlers-overview-windows-forms.md)
