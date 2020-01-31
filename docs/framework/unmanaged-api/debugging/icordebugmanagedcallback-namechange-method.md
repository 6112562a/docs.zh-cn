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
ms.openlocfilehash: 2d8fa00a1a998430a55b913cfa25624246eab967
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788362"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="53e8e-102">ICorDebugManagedCallback::NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="53e8e-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="53e8e-103">通知调试器应用程序域或线程的名称已更改。</span><span class="sxs-lookup"><span data-stu-id="53e8e-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e8e-104">语法</span><span class="sxs-lookup"><span data-stu-id="53e8e-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e8e-105">参数</span><span class="sxs-lookup"><span data-stu-id="53e8e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="53e8e-106">中指向 ICorDebugAppDomain 对象的指针，该对象表示具有名称更改或包含名称更改的线程的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="53e8e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="53e8e-107">中指向 ICorDebugThread 对象的指针，该对象表示名称发生更改的线程。</span><span class="sxs-lookup"><span data-stu-id="53e8e-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e8e-108">需求</span><span class="sxs-lookup"><span data-stu-id="53e8e-108">Requirements</span></span>  
 <span data-ttu-id="53e8e-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53e8e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e8e-110">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53e8e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53e8e-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e8e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e8e-112">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e8e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e8e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53e8e-113">See also</span></span>

- [<span data-ttu-id="53e8e-114">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="53e8e-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
