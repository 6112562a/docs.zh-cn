---
title: ISymUnmanagedDocumentWriter::SetSource 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da19a77637e64fec676fdaac7ba56d47b5b07769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549884"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="6808b-102">ISymUnmanagedDocumentWriter::SetSource 方法</span><span class="sxs-lookup"><span data-stu-id="6808b-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="6808b-103">正在写入的文档集将嵌入的源。</span><span class="sxs-lookup"><span data-stu-id="6808b-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6808b-104">语法</span><span class="sxs-lookup"><span data-stu-id="6808b-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6808b-105">参数</span><span class="sxs-lookup"><span data-stu-id="6808b-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="6808b-106">[in]一个`ULONG32`，其中包含的大小`source`缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6808b-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="6808b-107">[in]存储的嵌入的源缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6808b-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6808b-108">返回值</span><span class="sxs-lookup"><span data-stu-id="6808b-108">Return Value</span></span>  
 <span data-ttu-id="6808b-109">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="6808b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6808b-110">要求</span><span class="sxs-lookup"><span data-stu-id="6808b-110">Requirements</span></span>  
 <span data-ttu-id="6808b-111">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6808b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6808b-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="6808b-112">See also</span></span>
- [<span data-ttu-id="6808b-113">ISymUnmanagedDocumentWriter 接口</span><span class="sxs-lookup"><span data-stu-id="6808b-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
