---
title: ISymUnmanagedReader::ReplaceSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b863816bfb7ed1a5db1fa2234db224b01cb6c9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481542"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="49fc0-102">ISymUnmanagedReader::ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="49fc0-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="49fc0-103">用增量符号存储区替换现有的符号存储区。</span><span class="sxs-lookup"><span data-stu-id="49fc0-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="49fc0-104">此方法是类似于[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法，只不过给定的增量充当完全替换而不是更新。</span><span class="sxs-lookup"><span data-stu-id="49fc0-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49fc0-105">你需要仅指定一个`filename`或`pIStream`参数不可同时使用两者。</span><span class="sxs-lookup"><span data-stu-id="49fc0-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="49fc0-106">如果`filename`指定，则将使用该文件中的符号更新符号存储区。</span><span class="sxs-lookup"><span data-stu-id="49fc0-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="49fc0-107">如果`pIStream`中的数据将更新存储的指定<xref:System.Runtime.InteropServices.ComTypes.IStream>。</span><span class="sxs-lookup"><span data-stu-id="49fc0-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fc0-108">语法</span><span class="sxs-lookup"><span data-stu-id="49fc0-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49fc0-109">参数</span><span class="sxs-lookup"><span data-stu-id="49fc0-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="49fc0-110">[in]包含符号存储区的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="49fc0-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="49fc0-111">[in]作为一种替代方法使用的文件流`filename`参数。</span><span class="sxs-lookup"><span data-stu-id="49fc0-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49fc0-112">返回值</span><span class="sxs-lookup"><span data-stu-id="49fc0-112">Return Value</span></span>  
 <span data-ttu-id="49fc0-113">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="49fc0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49fc0-114">要求</span><span class="sxs-lookup"><span data-stu-id="49fc0-114">Requirements</span></span>  
 <span data-ttu-id="49fc0-115">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49fc0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49fc0-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="49fc0-116">See also</span></span>
- [<span data-ttu-id="49fc0-117">ISymUnmanagedReader 接口</span><span class="sxs-lookup"><span data-stu-id="49fc0-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
