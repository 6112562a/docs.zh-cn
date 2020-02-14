---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 6e4f0074958e8a6a8ca322968e9c29e89481c0c8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216518"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="8bfa4-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="8bfa4-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="8bfa4-103">当尝试通过 vtable 对已标记为仅后期绑定的类接口进行早期绑定调用时，则会激活 `dirtyCastAndCallOnInterface` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8bfa4-104">症状</span><span class="sxs-lookup"><span data-stu-id="8bfa4-104">Symptoms</span></span>  
 <span data-ttu-id="8bfa4-105">当通过 COM 将早期绑定调用放入 CLR 时，应用程序会引发访问冲突或产生意外行为。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8bfa4-106">原因</span><span class="sxs-lookup"><span data-stu-id="8bfa4-106">Cause</span></span>  
 <span data-ttu-id="8bfa4-107">代码正经由仅后期绑定的类接口尝试通过 vtable 进行早期绑定调用。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="8bfa4-108">请注意，默认情况下，类接口标识为仅后期绑定。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="8bfa4-109">也可通过具有 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 值 (<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>) 的 `[ClassInterface(ClassInterfaceType.AutoDispatch)]` 特性将它们识别为后期绑定。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8bfa4-110">解决方法</span><span class="sxs-lookup"><span data-stu-id="8bfa4-110">Resolution</span></span>  
 <span data-ttu-id="8bfa4-111">建议的解决方法是定义供 COM 使用的显式接口，并让 COM 客户端可以通过此接口而非自动生成的类接口进行调用。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="8bfa4-112">或者，从 COM 进行的调用可以经由 `IDispatch` 转换为后期绑定调用。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="8bfa4-113">最后，可将类标识为 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`)，以便可从 COM 放置早期绑定的调用；但是，由于 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> 中所述的版本管理限制，强烈建议不要使用 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8bfa4-114">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="8bfa4-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="8bfa4-115">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8bfa4-116">它仅报告对后期绑定接口的早期绑定调用的数据。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8bfa4-117">输出</span><span class="sxs-lookup"><span data-stu-id="8bfa4-117">Output</span></span>  
 <span data-ttu-id="8bfa4-118">按早期绑定访问的方法的名称或字段的名称。</span><span class="sxs-lookup"><span data-stu-id="8bfa4-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8bfa4-119">配置</span><span class="sxs-lookup"><span data-stu-id="8bfa4-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bfa4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bfa4-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="8bfa4-121">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="8bfa4-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
