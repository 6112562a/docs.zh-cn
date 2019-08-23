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
ms.openlocfilehash: d86f4bbec8971d164966298734388f0744a2d41c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953027"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="b7b5a-102">ICorDebugStepper2 接口</span><span class="sxs-lookup"><span data-stu-id="b7b5a-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="b7b5a-103">为 "仅我的代码" (JMC) 调试提供支持。</span><span class="sxs-lookup"><span data-stu-id="b7b5a-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7b5a-104">方法</span><span class="sxs-lookup"><span data-stu-id="b7b5a-104">Methods</span></span>  
  
|<span data-ttu-id="b7b5a-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7b5a-105">Method</span></span>|<span data-ttu-id="b7b5a-106">描述</span><span class="sxs-lookup"><span data-stu-id="b7b5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7b5a-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="b7b5a-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="b7b5a-108">设置一个值, 该值指定此 ICorDebugStepper 是否仅通过应用程序开发人员编写的代码执行步骤。</span><span class="sxs-lookup"><span data-stu-id="b7b5a-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7b5a-109">备注</span><span class="sxs-lookup"><span data-stu-id="b7b5a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7b5a-110">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="b7b5a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b5a-111">要求</span><span class="sxs-lookup"><span data-stu-id="b7b5a-111">Requirements</span></span>  
 <span data-ttu-id="b7b5a-112">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b5a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b5a-113">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="b7b5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7b5a-114">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7b5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7b5a-115">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b5a-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="b7b5a-116">See also</span></span>

- [<span data-ttu-id="b7b5a-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="b7b5a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
