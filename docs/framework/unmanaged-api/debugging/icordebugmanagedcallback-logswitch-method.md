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
ms.openlocfilehash: f095bc0272e0e6f16467b9758d5e392d371139dd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212680"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="bdec9-102">ICorDebugManagedCallback::LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="bdec9-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="bdec9-103">通知调试器公共语言运行时（CLR）托管线程已调用类中的方法 <xref:System.Diagnostics.Switch> 来创建、修改或删除调试/跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="bdec9-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdec9-104">语法</span><span class="sxs-lookup"><span data-stu-id="bdec9-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdec9-105">参数</span><span class="sxs-lookup"><span data-stu-id="bdec9-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="bdec9-106">中指向 ICorDebugAppDomain 对象的指针，该对象表示包含创建、修改或删除调试/跟踪开关的托管线程的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="bdec9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bdec9-107">中指向 ICorDebugThread 对象的指针，该对象表示托管线程。</span><span class="sxs-lookup"><span data-stu-id="bdec9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="bdec9-108">中一个值，该值指示写入事件日志的描述性消息的严重性级别。</span><span class="sxs-lookup"><span data-stu-id="bdec9-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="bdec9-109">中[LogSwitchCallReason](logswitchcallreason-enumeration.md)枚举的值，该值指示在调试/跟踪开关上执行的操作。</span><span class="sxs-lookup"><span data-stu-id="bdec9-109">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="bdec9-110">中指向调试/跟踪开关的名称的指针。</span><span class="sxs-lookup"><span data-stu-id="bdec9-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="bdec9-111">中一个指针，指向调试/跟踪开关的父项的名称。</span><span class="sxs-lookup"><span data-stu-id="bdec9-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdec9-112">要求</span><span class="sxs-lookup"><span data-stu-id="bdec9-112">Requirements</span></span>  
 <span data-ttu-id="bdec9-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdec9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdec9-114">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdec9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdec9-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdec9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdec9-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdec9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdec9-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdec9-117">See also</span></span>

- [<span data-ttu-id="bdec9-118">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="bdec9-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
