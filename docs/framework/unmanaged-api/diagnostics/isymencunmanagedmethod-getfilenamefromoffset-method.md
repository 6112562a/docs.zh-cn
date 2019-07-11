---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bfdc9d58a86bb4cf945f0c8106bcfc00f3743e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760314"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="00413-102">ISymENCUnmanagedMethod::GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="00413-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="00413-103">获取与某一偏移量关联的行的文件名称。</span><span class="sxs-lookup"><span data-stu-id="00413-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00413-104">语法</span><span class="sxs-lookup"><span data-stu-id="00413-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00413-105">参数</span><span class="sxs-lookup"><span data-stu-id="00413-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="00413-106">[in]一个`ULONG32`包含的偏移量。</span><span class="sxs-lookup"><span data-stu-id="00413-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="00413-107">[in]一个`ULONG32`指示的大小`szName`缓冲区。</span><span class="sxs-lookup"><span data-stu-id="00413-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="00413-108">[out]一个指向`ULONG32`用于接收大小，以字符为单位，以包含文件名称的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="00413-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="00413-109">[out]包含文件名称的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="00413-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00413-110">返回值</span><span class="sxs-lookup"><span data-stu-id="00413-110">Return Value</span></span>  
 <span data-ttu-id="00413-111">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="00413-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00413-112">要求</span><span class="sxs-lookup"><span data-stu-id="00413-112">Requirements</span></span>  
 <span data-ttu-id="00413-113">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00413-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00413-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="00413-114">See also</span></span>

- [<span data-ttu-id="00413-115">ISymENCUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="00413-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
