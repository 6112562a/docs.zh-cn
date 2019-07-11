---
title: ICorDebugManagedCallback::LogSwitch 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d7432771a7d8eee9cea10f883dd3bd91f5ffb74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761387"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="e3af9-102">ICorDebugManagedCallback::LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="e3af9-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="e3af9-103">通知调试器公共语言运行时 (CLR) 托管线程已调用的一个方法<xref:System.Diagnostics.Switch>类来创建、 修改或删除调试/跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="e3af9-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3af9-104">语法</span><span class="sxs-lookup"><span data-stu-id="e3af9-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3af9-105">参数</span><span class="sxs-lookup"><span data-stu-id="e3af9-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="e3af9-106">[in]指向一个 ICorDebugAppDomain 对象，表示包含创建、 修改或删除调试/跟踪开关的托管的线程的应用程序域的指针。</span><span class="sxs-lookup"><span data-stu-id="e3af9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e3af9-107">[in]指向表示托管的线程的 ICorDebugThread 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="e3af9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="e3af9-108">[in]一个值，指示已写入事件日志的描述性消息的严重性级别。</span><span class="sxs-lookup"><span data-stu-id="e3af9-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="e3af9-109">[in]值为[LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)上调试/跟踪开关执行枚举，指示该操作。</span><span class="sxs-lookup"><span data-stu-id="e3af9-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="e3af9-110">[in]指向调试/跟踪开关的名称的指针。</span><span class="sxs-lookup"><span data-stu-id="e3af9-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="e3af9-111">[in]指向调试/跟踪开关的父级的名称的指针。</span><span class="sxs-lookup"><span data-stu-id="e3af9-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3af9-112">要求</span><span class="sxs-lookup"><span data-stu-id="e3af9-112">Requirements</span></span>  
 <span data-ttu-id="e3af9-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3af9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3af9-114">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3af9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3af9-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3af9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3af9-116">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3af9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3af9-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="e3af9-117">See also</span></span>

- [<span data-ttu-id="e3af9-118">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="e3af9-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
