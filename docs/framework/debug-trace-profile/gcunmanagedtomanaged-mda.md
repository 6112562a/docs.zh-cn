---
title: gcUnmanagedToManaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: dd4080870ae88da8d4e2055369cd36f3981f2eac
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216458"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="1bc02-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="1bc02-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="1bc02-103">每当一个线程从托管代码转换到非托管代码，`gcUnmanagedToManaged` 托管调试助手 (MDA) 就会导致垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="1bc02-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1bc02-104">症状</span><span class="sxs-lookup"><span data-stu-id="1bc02-104">Symptoms</span></span>  
 <span data-ttu-id="1bc02-105">使用 COM 和平台调用来运行非托管用户组件的应用程序在 CLR 中导致了一个非确定性的访问冲突。</span><span class="sxs-lookup"><span data-stu-id="1bc02-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1bc02-106">原因</span><span class="sxs-lookup"><span data-stu-id="1bc02-106">Cause</span></span>  
 <span data-ttu-id="1bc02-107">如果一个应用程序运行非托管用户组件，则这些组件可能损坏了已垃圾回收的堆。</span><span class="sxs-lookup"><span data-stu-id="1bc02-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="1bc02-108">在垃圾回收器尝试审核对象图时，这会在 CLR 中导致访问冲突。</span><span class="sxs-lookup"><span data-stu-id="1bc02-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1bc02-109">解决方法</span><span class="sxs-lookup"><span data-stu-id="1bc02-109">Resolution</span></span>  
 <span data-ttu-id="1bc02-110">通过在每次托管转换之前强制垃圾回收来启用此助手，可以减少从非托管组件损坏已垃圾回收的堆到发生访问冲突之间的时间。</span><span class="sxs-lookup"><span data-stu-id="1bc02-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1bc02-111">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="1bc02-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="1bc02-112">导致每当发生从非托管代码到托管代码的线程转换时都进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="1bc02-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1bc02-113">输出</span><span class="sxs-lookup"><span data-stu-id="1bc02-113">Output</span></span>  
 <span data-ttu-id="1bc02-114">此 MDA 不会产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="1bc02-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1bc02-115">配置</span><span class="sxs-lookup"><span data-stu-id="1bc02-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bc02-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bc02-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1bc02-117">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="1bc02-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1bc02-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="1bc02-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="1bc02-119">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="1bc02-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
