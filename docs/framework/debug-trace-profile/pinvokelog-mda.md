---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052380"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="9b307-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="9b307-102">pInvokeLog MDA</span></span>
<span data-ttu-id="9b307-103">`pInvokeLog` 托管调试助手 (MDA) 会为执行期间使用的每个唯一平台调用签名而激活。</span><span class="sxs-lookup"><span data-stu-id="9b307-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9b307-104">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="9b307-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="9b307-105">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="9b307-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9b307-106">Output</span><span class="sxs-lookup"><span data-stu-id="9b307-106">Output</span></span>  
 <span data-ttu-id="9b307-107">指示执行期间使用的平台调用签名的消息。</span><span class="sxs-lookup"><span data-stu-id="9b307-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9b307-108">配置</span><span class="sxs-lookup"><span data-stu-id="9b307-108">Configuration</span></span>  
 <span data-ttu-id="9b307-109">每个匹配元素筛选平台调用将进行调用的 .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="9b307-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b307-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b307-110">See also</span></span>

- [<span data-ttu-id="9b307-111">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="9b307-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9b307-112">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="9b307-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
