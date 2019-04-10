---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82f2f335299cfd3041dcecc7d176cb77ce54ae96
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172128"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="f6702-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="f6702-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="f6702-103">允许编译器忽略尚未修改的程序数据库 (PDB) 流中的函数，提供行信息满足要求。</span><span class="sxs-lookup"><span data-stu-id="f6702-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="f6702-104">可使用旧的 PDB 行信息和函数中的所有行的一个增量确定正确的行信息。</span><span class="sxs-lookup"><span data-stu-id="f6702-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6702-105">语法</span><span class="sxs-lookup"><span data-stu-id="f6702-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6702-106">参数</span><span class="sxs-lookup"><span data-stu-id="f6702-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="f6702-107">[in]一个指向[IStream](/windows/desktop/api/objidl/nn-objidl-istream)包含行信息。</span><span class="sxs-lookup"><span data-stu-id="f6702-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="f6702-108">[in]一个指向[SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)结构，其中包含已更改的行。</span><span class="sxs-lookup"><span data-stu-id="f6702-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="f6702-109">[in]一个`ULONG`，表示已更改的行数。</span><span class="sxs-lookup"><span data-stu-id="f6702-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6702-110">返回值</span><span class="sxs-lookup"><span data-stu-id="f6702-110">Return Value</span></span>  
 <span data-ttu-id="f6702-111">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="f6702-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6702-112">要求</span><span class="sxs-lookup"><span data-stu-id="f6702-112">Requirements</span></span>  
 <span data-ttu-id="f6702-113">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f6702-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6702-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6702-114">See also</span></span>

- [<span data-ttu-id="f6702-115">ISymUnmanagedENCUpdate 接口</span><span class="sxs-lookup"><span data-stu-id="f6702-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
