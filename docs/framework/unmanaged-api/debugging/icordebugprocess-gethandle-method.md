---
title: ICorDebugProcess::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56f1dd892429724866182248b0c0413a7d2437cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766071"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="95767-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="95767-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="95767-103">获取进程的句柄。</span><span class="sxs-lookup"><span data-stu-id="95767-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95767-104">语法</span><span class="sxs-lookup"><span data-stu-id="95767-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95767-105">参数</span><span class="sxs-lookup"><span data-stu-id="95767-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="95767-106">[out]一个指向`HPROCESS`，它是进程的句柄。</span><span class="sxs-lookup"><span data-stu-id="95767-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95767-107">备注</span><span class="sxs-lookup"><span data-stu-id="95767-107">Remarks</span></span>  
 <span data-ttu-id="95767-108">调试接口为所有检索到的句柄。</span><span class="sxs-lookup"><span data-stu-id="95767-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="95767-109">调试器应重复使用它之前的句柄。</span><span class="sxs-lookup"><span data-stu-id="95767-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95767-110">要求</span><span class="sxs-lookup"><span data-stu-id="95767-110">Requirements</span></span>  
 <span data-ttu-id="95767-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95767-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95767-112">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95767-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95767-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95767-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95767-114">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95767-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
