---
title: ISymUnmanagedMethod::GetRootScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8956d72d25f240eff653d3eefb92b68431f4e2ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771780"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="194fa-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="194fa-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="194fa-103">获取在此方法内的根词法范围。</span><span class="sxs-lookup"><span data-stu-id="194fa-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="194fa-104">此范围包括整个方法。</span><span class="sxs-lookup"><span data-stu-id="194fa-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194fa-105">语法</span><span class="sxs-lookup"><span data-stu-id="194fa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="194fa-106">参数</span><span class="sxs-lookup"><span data-stu-id="194fa-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="194fa-107">[out]一个指针，它设置为返回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="194fa-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="194fa-108">返回值</span><span class="sxs-lookup"><span data-stu-id="194fa-108">Return Value</span></span>  
 <span data-ttu-id="194fa-109">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="194fa-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="194fa-110">要求</span><span class="sxs-lookup"><span data-stu-id="194fa-110">Requirements</span></span>  
 <span data-ttu-id="194fa-111">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="194fa-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194fa-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="194fa-112">See also</span></span>

- [<span data-ttu-id="194fa-113">ISymUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="194fa-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
