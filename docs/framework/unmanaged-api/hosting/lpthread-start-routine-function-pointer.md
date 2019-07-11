---
title: LPTHREAD_START_ROUTINE 函数指针
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 577526536e07172070a1e8a65e73fd15646681fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768346"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="7c560-102">LPTHREAD_START_ROUTINE 函数指针</span><span class="sxs-lookup"><span data-stu-id="7c560-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="7c560-103">指向通知宿主某个线程已开始执行的函数。</span><span class="sxs-lookup"><span data-stu-id="7c560-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="7c560-104">.NET Framework 4 中已弃用此函数指针。</span><span class="sxs-lookup"><span data-stu-id="7c560-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c560-105">语法</span><span class="sxs-lookup"><span data-stu-id="7c560-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c560-106">参数</span><span class="sxs-lookup"><span data-stu-id="7c560-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="7c560-107">[in]指向已开始执行的代码的指针。</span><span class="sxs-lookup"><span data-stu-id="7c560-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c560-108">备注</span><span class="sxs-lookup"><span data-stu-id="7c560-108">Remarks</span></span>  
 <span data-ttu-id="7c560-109">该函数`LPTHREAD_START_ROUTINE`点是回调函数，必须由主机应用程序的编写器实现。</span><span class="sxs-lookup"><span data-stu-id="7c560-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c560-110">要求</span><span class="sxs-lookup"><span data-stu-id="7c560-110">Requirements</span></span>  
 <span data-ttu-id="7c560-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c560-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c560-112">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c560-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c560-113">**库：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="7c560-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="7c560-114">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c560-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c560-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c560-115">See also</span></span>

- [<span data-ttu-id="7c560-116">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="7c560-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
