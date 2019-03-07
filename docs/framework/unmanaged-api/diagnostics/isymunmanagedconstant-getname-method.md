---
title: ISymUnmanagedConstant::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e57ab385ce4d393b29ff5af867bf7a019bf2b824
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478929"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="ca939-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="ca939-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="ca939-103">获取常量的名称。</span><span class="sxs-lookup"><span data-stu-id="ca939-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca939-104">语法</span><span class="sxs-lookup"><span data-stu-id="ca939-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca939-105">参数</span><span class="sxs-lookup"><span data-stu-id="ca939-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ca939-106">[in]缓冲区的长度的`szName`参数指向。</span><span class="sxs-lookup"><span data-stu-id="ca939-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ca939-107">[out]一个指向`ULONG32`用于接收大小，以字符为单位，以包含名称，包括 null 终止的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ca939-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca939-108">[out]存储名称的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ca939-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca939-109">返回值</span><span class="sxs-lookup"><span data-stu-id="ca939-109">Return Value</span></span>  
 <span data-ttu-id="ca939-110">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="ca939-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca939-111">要求</span><span class="sxs-lookup"><span data-stu-id="ca939-111">Requirements</span></span>  
 <span data-ttu-id="ca939-112">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca939-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca939-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ca939-113">See also</span></span>
- [<span data-ttu-id="ca939-114">ISymUnmanagedConstant 接口</span><span class="sxs-lookup"><span data-stu-id="ca939-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="ca939-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="ca939-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="ca939-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="ca939-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
