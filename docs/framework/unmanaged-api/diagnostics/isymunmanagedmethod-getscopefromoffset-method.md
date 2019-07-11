---
title: ISymUnmanagedMethod::GetScopeFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d540318dabd55e9a520aedde371e0a83d612721e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759486"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="f8647-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f8647-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="f8647-103">获取包含给定的偏移量此方法中最封闭的词法范围。</span><span class="sxs-lookup"><span data-stu-id="f8647-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="f8647-104">这可用来启动本地变量的搜索。</span><span class="sxs-lookup"><span data-stu-id="f8647-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8647-105">语法</span><span class="sxs-lookup"><span data-stu-id="f8647-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8647-106">参数</span><span class="sxs-lookup"><span data-stu-id="f8647-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f8647-107">[in]一个`ULONG`包含的偏移量。</span><span class="sxs-lookup"><span data-stu-id="f8647-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f8647-108">[out]一个指针，它设置为返回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="f8647-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8647-109">返回值</span><span class="sxs-lookup"><span data-stu-id="f8647-109">Return Value</span></span>  
 <span data-ttu-id="f8647-110">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="f8647-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8647-111">要求</span><span class="sxs-lookup"><span data-stu-id="f8647-111">Requirements</span></span>  
 <span data-ttu-id="f8647-112">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8647-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8647-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8647-113">See also</span></span>

- [<span data-ttu-id="f8647-114">ISymUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="f8647-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
