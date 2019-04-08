---
title: ICorDebugStepper2 接口
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073042"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="3f47f-102">ICorDebugStepper2 接口</span><span class="sxs-lookup"><span data-stu-id="3f47f-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="3f47f-103">仅我的代码 (JMC) 调试提供支持。</span><span class="sxs-lookup"><span data-stu-id="3f47f-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f47f-104">方法</span><span class="sxs-lookup"><span data-stu-id="3f47f-104">Methods</span></span>  
  
|<span data-ttu-id="3f47f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3f47f-105">Method</span></span>|<span data-ttu-id="3f47f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3f47f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f47f-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="3f47f-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="3f47f-108">设置一个值，指定是否有此 ICorDebugStepper 步骤只能通过由应用程序的开发人员编写的代码。</span><span class="sxs-lookup"><span data-stu-id="3f47f-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f47f-109">备注</span><span class="sxs-lookup"><span data-stu-id="3f47f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f47f-110">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="3f47f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f47f-111">要求</span><span class="sxs-lookup"><span data-stu-id="3f47f-111">Requirements</span></span>  
 <span data-ttu-id="3f47f-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f47f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f47f-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f47f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f47f-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f47f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3f47f-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3f47f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f47f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f47f-116">See also</span></span>

- [<span data-ttu-id="3f47f-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="3f47f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
