---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052786"
---
# <a name="failedqi-mda"></a><span data-ttu-id="78cea-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="78cea-102">failedQI MDA</span></span>
<span data-ttu-id="78cea-103">当运行时代表运行时可调用包装器 (RCW) 在 COM 接口指针上调用 `QueryInterface` 且 `QueryInterface` 调用失败时，将激活 `failedQI` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="78cea-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="78cea-104">症状</span><span class="sxs-lookup"><span data-stu-id="78cea-104">Symptoms</span></span>  
 <span data-ttu-id="78cea-105">对 RCW 的强制转换失败，或从 RCW 调用 COM 意外失败。</span><span class="sxs-lookup"><span data-stu-id="78cea-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="78cea-106">原因</span><span class="sxs-lookup"><span data-stu-id="78cea-106">Cause</span></span>  
  
- <span data-ttu-id="78cea-107">从错误的上下文进行调用。</span><span class="sxs-lookup"><span data-stu-id="78cea-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="78cea-108">注册的代理将无法进行 `QueryInterface` 调用，因为尝试在错误的上下文中进行调用。</span><span class="sxs-lookup"><span data-stu-id="78cea-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="78cea-109">OLE 拥有的代理返回失败 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="78cea-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="78cea-110">解决方法</span><span class="sxs-lookup"><span data-stu-id="78cea-110">Resolution</span></span>  
 <span data-ttu-id="78cea-111">请参阅 MSDN 文档的 COM 规则部分。</span><span class="sxs-lookup"><span data-stu-id="78cea-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="78cea-112">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="78cea-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="78cea-113">如果 `QueryInterface` 调用失败，将切换上下文并再次尝试调用`QueryInterface`，以确定是否因上下文错误而引起。</span><span class="sxs-lookup"><span data-stu-id="78cea-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="78cea-114">Output</span><span class="sxs-lookup"><span data-stu-id="78cea-114">Output</span></span>  
 <span data-ttu-id="78cea-115">接口的托管名称、接口的 GUID 和失败的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="78cea-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="78cea-116">配置</span><span class="sxs-lookup"><span data-stu-id="78cea-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78cea-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="78cea-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="78cea-118">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="78cea-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="78cea-119">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="78cea-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
