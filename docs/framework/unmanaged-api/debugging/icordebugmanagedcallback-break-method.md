---
title: ICorDebugManagedCallback::Break 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: efc9de050e34867c14f8e85e091e2b959c30f213
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122587"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="de6b8-102">ICorDebugManagedCallback::Break 方法</span><span class="sxs-lookup"><span data-stu-id="de6b8-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="de6b8-103">当执行代码流中的 <xref:System.Reflection.Emit.OpCodes.Break> 指令时，通知调试器。</span><span class="sxs-lookup"><span data-stu-id="de6b8-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="de6b8-104">语法</span><span class="sxs-lookup"><span data-stu-id="de6b8-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="de6b8-105">参数</span><span class="sxs-lookup"><span data-stu-id="de6b8-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="de6b8-106">中指向 ICorDebugAppDomain 对象的指针，该对象表示包含中断指令的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="de6b8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="de6b8-107">中指向 ICorDebugThread 对象的指针，该对象表示包含中断指令的线程。</span><span class="sxs-lookup"><span data-stu-id="de6b8-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="de6b8-108">要求</span><span class="sxs-lookup"><span data-stu-id="de6b8-108">Requirements</span></span>

<span data-ttu-id="de6b8-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de6b8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="de6b8-110">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de6b8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="de6b8-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de6b8-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="de6b8-112">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6b8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="de6b8-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="de6b8-113">See also</span></span>

- [<span data-ttu-id="de6b8-114">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="de6b8-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
