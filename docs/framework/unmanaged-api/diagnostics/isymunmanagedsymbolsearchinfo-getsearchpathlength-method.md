---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27de34c1978818c48d5fa38caf9b52ff2a9510f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778082"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="14571-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="14571-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="14571-103">获取搜索路径长度。</span><span class="sxs-lookup"><span data-stu-id="14571-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14571-104">语法</span><span class="sxs-lookup"><span data-stu-id="14571-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14571-105">参数</span><span class="sxs-lookup"><span data-stu-id="14571-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="14571-106">[out]一个指向`ULONG32`用于接收大小，以字符为单位，以包含搜索路径长度的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="14571-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14571-107">返回值</span><span class="sxs-lookup"><span data-stu-id="14571-107">Return Value</span></span>  
 <span data-ttu-id="14571-108">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="14571-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14571-109">要求</span><span class="sxs-lookup"><span data-stu-id="14571-109">Requirements</span></span>  
 <span data-ttu-id="14571-110">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="14571-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14571-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="14571-111">See also</span></span>

- [<span data-ttu-id="14571-112">ISymUnmanagedSymbolSearchInfo 接口</span><span class="sxs-lookup"><span data-stu-id="14571-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
