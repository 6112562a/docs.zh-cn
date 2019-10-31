---
title: ICorDebugMDA 接口
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129789"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="8713b-102">ICorDebugMDA 接口</span><span class="sxs-lookup"><span data-stu-id="8713b-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="8713b-103">表示托管调试助手 (MDA) 消息。</span><span class="sxs-lookup"><span data-stu-id="8713b-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8713b-104">方法</span><span class="sxs-lookup"><span data-stu-id="8713b-104">Methods</span></span>  
  
|<span data-ttu-id="8713b-105">方法</span><span class="sxs-lookup"><span data-stu-id="8713b-105">Method</span></span>|<span data-ttu-id="8713b-106">描述</span><span class="sxs-lookup"><span data-stu-id="8713b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8713b-107">GetDescription 方法</span><span class="sxs-lookup"><span data-stu-id="8713b-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="8713b-108">获取一个字符串，该字符串包含此 MDA 的说明。</span><span class="sxs-lookup"><span data-stu-id="8713b-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="8713b-109">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="8713b-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="8713b-110">获取与此 MDA 关联的标志。</span><span class="sxs-lookup"><span data-stu-id="8713b-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="8713b-111">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="8713b-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="8713b-112">获取包含此 MDA 的名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="8713b-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="8713b-113">GetOSThreadId 方法</span><span class="sxs-lookup"><span data-stu-id="8713b-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="8713b-114">获取要在其上执行此 MDA 的操作系统线程标识符。</span><span class="sxs-lookup"><span data-stu-id="8713b-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="8713b-115">GetXML 方法</span><span class="sxs-lookup"><span data-stu-id="8713b-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="8713b-116">获取与此 MDA 关联的完整 XML 流。</span><span class="sxs-lookup"><span data-stu-id="8713b-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8713b-117">备注</span><span class="sxs-lookup"><span data-stu-id="8713b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8713b-118">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="8713b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8713b-119">要求</span><span class="sxs-lookup"><span data-stu-id="8713b-119">Requirements</span></span>  
 <span data-ttu-id="8713b-120">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8713b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8713b-121">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8713b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8713b-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8713b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8713b-123">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8713b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8713b-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="8713b-124">See also</span></span>

- [<span data-ttu-id="8713b-125">调试接口</span><span class="sxs-lookup"><span data-stu-id="8713b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8713b-126">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="8713b-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
