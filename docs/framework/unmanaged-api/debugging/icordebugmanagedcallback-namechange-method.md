---
title: ICorDebugManagedCallback::NameChange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abbfd21736d220f1cba029235c71a85bf3048ff0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761617"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="5932b-102">ICorDebugManagedCallback::NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="5932b-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="5932b-103">通知调试器的应用程序域或线程名称已更改。</span><span class="sxs-lookup"><span data-stu-id="5932b-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5932b-104">语法</span><span class="sxs-lookup"><span data-stu-id="5932b-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5932b-105">参数</span><span class="sxs-lookup"><span data-stu-id="5932b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5932b-106">[in]指向 ICorDebugAppDomain 对象表示应用程序域的名称更改或，或者必须包含有名称的更改的线程。</span><span class="sxs-lookup"><span data-stu-id="5932b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5932b-107">[in]指向表示发生了名称更改的线程的 ICorDebugThread 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="5932b-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5932b-108">要求</span><span class="sxs-lookup"><span data-stu-id="5932b-108">Requirements</span></span>  
 <span data-ttu-id="5932b-109">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5932b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5932b-110">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5932b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5932b-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5932b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5932b-112">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5932b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5932b-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="5932b-113">See also</span></span>

- [<span data-ttu-id="5932b-114">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="5932b-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
