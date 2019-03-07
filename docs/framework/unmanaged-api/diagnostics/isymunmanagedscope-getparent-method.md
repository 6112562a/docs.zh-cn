---
title: ISymUnmanagedScope::GetParent 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634f30186c552f0e5330dd94f78c585da7d450c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493825"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="91b18-102">ISymUnmanagedScope::GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="91b18-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="91b18-103">获取此作用域的父作用域。</span><span class="sxs-lookup"><span data-stu-id="91b18-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b18-104">语法</span><span class="sxs-lookup"><span data-stu-id="91b18-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b18-105">参数</span><span class="sxs-lookup"><span data-stu-id="91b18-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="91b18-106">[out]指向返回的指针[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="91b18-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91b18-107">返回值</span><span class="sxs-lookup"><span data-stu-id="91b18-107">Return Value</span></span>  
 <span data-ttu-id="91b18-108">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="91b18-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b18-109">要求</span><span class="sxs-lookup"><span data-stu-id="91b18-109">Requirements</span></span>  
 <span data-ttu-id="91b18-110">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="91b18-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b18-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="91b18-111">See also</span></span>
- [<span data-ttu-id="91b18-112">ISymUnmanagedScope 接口</span><span class="sxs-lookup"><span data-stu-id="91b18-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="91b18-113">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="91b18-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
