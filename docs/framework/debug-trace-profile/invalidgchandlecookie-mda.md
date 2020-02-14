---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216311"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="4fac3-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="4fac3-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="4fac3-103">尝试将无效的 `invalidGCHandleCookie` Cookie 转换为 <xref:System.IntPtr> 时，将激活 <xref:System.Runtime.InteropServices.GCHandle> 托管调试助手（MDA）。</span><span class="sxs-lookup"><span data-stu-id="4fac3-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4fac3-104">症状</span><span class="sxs-lookup"><span data-stu-id="4fac3-104">Symptoms</span></span>  
 <span data-ttu-id="4fac3-105">尝试从 <xref:System.Runtime.InteropServices.GCHandle> 使用或检索 <xref:System.IntPtr> 时，发生未定义的行为，如访问冲突和内存损坏。</span><span class="sxs-lookup"><span data-stu-id="4fac3-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4fac3-106">原因</span><span class="sxs-lookup"><span data-stu-id="4fac3-106">Cause</span></span>  
 <span data-ttu-id="4fac3-107">该 Cookie 可能是无效的，因为它原本不是从 <xref:System.Runtime.InteropServices.GCHandle> 创建的。它表示已被释放的 <xref:System.Runtime.InteropServices.GCHandle>，是不同应用程序域中 <xref:System.Runtime.InteropServices.GCHandle> 的 Cookie，或者作为 <xref:System.Runtime.InteropServices.GCHandle> 被封送到了本机代码、但作为 <xref:System.IntPtr> 被传回到了 CLR，在那里尝试了转换。</span><span class="sxs-lookup"><span data-stu-id="4fac3-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4fac3-108">解决方法</span><span class="sxs-lookup"><span data-stu-id="4fac3-108">Resolution</span></span>  
 <span data-ttu-id="4fac3-109">为 <xref:System.IntPtr> 指定有效的 <xref:System.Runtime.InteropServices.GCHandle> Cookie。</span><span class="sxs-lookup"><span data-stu-id="4fac3-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4fac3-110">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="4fac3-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="4fac3-111">此 MDA 启用后，调试程序不再能从根源追溯到对象，因为传回的 Cookie 值与 MDA 未启用时返回的值不同。</span><span class="sxs-lookup"><span data-stu-id="4fac3-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4fac3-112">输出</span><span class="sxs-lookup"><span data-stu-id="4fac3-112">Output</span></span>  
 <span data-ttu-id="4fac3-113">报告无效的 <xref:System.IntPtr> Cookie 值。</span><span class="sxs-lookup"><span data-stu-id="4fac3-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4fac3-114">配置</span><span class="sxs-lookup"><span data-stu-id="4fac3-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fac3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fac3-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="4fac3-116">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="4fac3-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
