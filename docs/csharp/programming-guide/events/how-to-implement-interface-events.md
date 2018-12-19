---
title: 如何：实现接口事件 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: d52d4d5140e96f81377733e39d1c36886718b706
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236435"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="a5b4b-102">如何：实现接口事件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="a5b4b-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="a5b4b-103">[接口](../../../csharp/language-reference/keywords/interface.md)可以声明[事件](../../../csharp/language-reference/keywords/event.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="a5b4b-104">下面的示例演示如何在类中实现接口事件。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="a5b4b-105">这些规则基本上都与实现任何接口方法或属性时的相同。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="a5b4b-106">在类中实现接口事件</span><span class="sxs-lookup"><span data-stu-id="a5b4b-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="a5b4b-107">在类中声明事件，然后在相应区域中调用它。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs   
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.   
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="a5b4b-108">示例</span><span class="sxs-lookup"><span data-stu-id="a5b4b-108">Example</span></span>  
<span data-ttu-id="a5b4b-109">下面的示例演示如何处理不太常见的情况：类继承自两个或多个接口，且每个接口都具有相同名称的事件。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="a5b4b-110">在这种情况下，你必须为至少其中一个事件提供显式接口实现。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="a5b4b-111">为事件编写显式接口实现时，还必须编写 `add` 和 `remove` 事件访问器。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="a5b4b-112">通常这些访问器由编译器提供，但在这种情况下编译器不提供它们。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="a5b4b-113">通过提供自己的访问器，可以指定两个事件是由类中的同一个事件表示，还是由不同事件表示。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="a5b4b-114">例如，如果根据接口规范应在不同时间引发事件，可以在类中将每个事件与单独实现关联。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="a5b4b-115">在下面的示例中，订阅服务器确定它们通过将形状引用转换为 `IShape` 或 `IDrawingObject` 接收哪个 `OnDraw` 事件。</span><span class="sxs-lookup"><span data-stu-id="a5b4b-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a><span data-ttu-id="a5b4b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="a5b4b-116">See Also</span></span>

- [<span data-ttu-id="a5b4b-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="a5b4b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a5b4b-118">事件</span><span class="sxs-lookup"><span data-stu-id="a5b4b-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="a5b4b-119">委托</span><span class="sxs-lookup"><span data-stu-id="a5b4b-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="a5b4b-120">显式接口实现</span><span class="sxs-lookup"><span data-stu-id="a5b4b-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [<span data-ttu-id="a5b4b-121">如何：在派生类中抛出基类事件</span><span class="sxs-lookup"><span data-stu-id="a5b4b-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
