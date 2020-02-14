---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 8a0c72cf26ef8434719ff6661ef15a44f51c8740
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217262"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="17d50-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="17d50-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="17d50-103">如果在重叠操作完成之前调用 `overlappedFreeError` 方法，将激活 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="17d50-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="17d50-104">症状</span><span class="sxs-lookup"><span data-stu-id="17d50-104">Symptoms</span></span>  
 <span data-ttu-id="17d50-105">访问冲突或垃圾回收堆损坏。</span><span class="sxs-lookup"><span data-stu-id="17d50-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="17d50-106">原因</span><span class="sxs-lookup"><span data-stu-id="17d50-106">Cause</span></span>  
 <span data-ttu-id="17d50-107">操作完成之前，已释放重叠结构。</span><span class="sxs-lookup"><span data-stu-id="17d50-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="17d50-108">使用重叠指针的函数可能稍后会在释放结构后写入结构。</span><span class="sxs-lookup"><span data-stu-id="17d50-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="17d50-109">由于另一个对象当前可能占用该区域，这可能会导致堆损坏。</span><span class="sxs-lookup"><span data-stu-id="17d50-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="17d50-110">如果重叠操作未成功开始，则此 MDA 可能不表示错误。</span><span class="sxs-lookup"><span data-stu-id="17d50-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="17d50-111">解决方法</span><span class="sxs-lookup"><span data-stu-id="17d50-111">Resolution</span></span>  
 <span data-ttu-id="17d50-112">在调用 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> 方法之前，确保已完成使用重叠结构的 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="17d50-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="17d50-113">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="17d50-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="17d50-114">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="17d50-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="17d50-115">输出</span><span class="sxs-lookup"><span data-stu-id="17d50-115">Output</span></span>  
 <span data-ttu-id="17d50-116">以下是此 MDA 的示例输出。</span><span class="sxs-lookup"><span data-stu-id="17d50-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="17d50-117">配置</span><span class="sxs-lookup"><span data-stu-id="17d50-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17d50-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17d50-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="17d50-119">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="17d50-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="17d50-120">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="17d50-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
