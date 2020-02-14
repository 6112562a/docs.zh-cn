---
title: notMarshalable MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217288"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="12ba7-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="12ba7-102">notMarshalable MDA</span></span>
<span data-ttu-id="12ba7-103">当公共语言运行时 (CLR) 尝试跨上下文封送接口时，如果遇到 COM 接口指针且没有有效的注册代理/存根或 `notMarshalable` 接口实现不正确，将激活 `IMarshal` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="12ba7-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="12ba7-104">症状</span><span class="sxs-lookup"><span data-stu-id="12ba7-104">Symptoms</span></span>  
 <span data-ttu-id="12ba7-105">调用得不到响应，或在 COM 接口指针的错误上下文中进行调用。</span><span class="sxs-lookup"><span data-stu-id="12ba7-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="12ba7-106">原因</span><span class="sxs-lookup"><span data-stu-id="12ba7-106">Cause</span></span>  
 <span data-ttu-id="12ba7-107">尝试跨上下文封送接口时，没有有效的注册代理/存根或 `IMarshal` 不正确。</span><span class="sxs-lookup"><span data-stu-id="12ba7-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="12ba7-108">解决方法</span><span class="sxs-lookup"><span data-stu-id="12ba7-108">Resolution</span></span>  
 <span data-ttu-id="12ba7-109">请确保注册了代理存根，且 `IMarshal` 实现有效。</span><span class="sxs-lookup"><span data-stu-id="12ba7-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="12ba7-110">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="12ba7-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="12ba7-111">此 MDA 对运行时无任何影响。</span><span class="sxs-lookup"><span data-stu-id="12ba7-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="12ba7-112">输出</span><span class="sxs-lookup"><span data-stu-id="12ba7-112">Output</span></span>  
 <span data-ttu-id="12ba7-113">描述问题的消息。</span><span class="sxs-lookup"><span data-stu-id="12ba7-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="12ba7-114">配置</span><span class="sxs-lookup"><span data-stu-id="12ba7-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12ba7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12ba7-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="12ba7-116">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="12ba7-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="12ba7-117">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="12ba7-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
