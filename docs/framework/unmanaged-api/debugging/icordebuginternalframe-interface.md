---
title: ICorDebugInternalFrame 接口
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910160"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="7e045-102">ICorDebugInternalFrame 接口</span><span class="sxs-lookup"><span data-stu-id="7e045-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="7e045-103">表示堆栈上的运行时内部帧。</span><span class="sxs-lookup"><span data-stu-id="7e045-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="7e045-104">此接口是 ICorDebugFrame 接口的子类。</span><span class="sxs-lookup"><span data-stu-id="7e045-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e045-105">方法</span><span class="sxs-lookup"><span data-stu-id="7e045-105">Methods</span></span>  
  
|<span data-ttu-id="7e045-106">方法</span><span class="sxs-lookup"><span data-stu-id="7e045-106">Method</span></span>|<span data-ttu-id="7e045-107">描述</span><span class="sxs-lookup"><span data-stu-id="7e045-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e045-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="7e045-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="7e045-109">获取此内部帧的类型。</span><span class="sxs-lookup"><span data-stu-id="7e045-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e045-110">备注</span><span class="sxs-lookup"><span data-stu-id="7e045-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e045-111">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="7e045-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e045-112">要求</span><span class="sxs-lookup"><span data-stu-id="7e045-112">Requirements</span></span>  
 <span data-ttu-id="7e045-113">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e045-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e045-114">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="7e045-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e045-115">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e045-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e045-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e045-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e045-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="7e045-117">See also</span></span>

- [<span data-ttu-id="7e045-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="7e045-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
