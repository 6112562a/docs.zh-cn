---
title: ISymUnmanagedReader::Initialize 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1986ed730c6f0a1ba8a2d8e3c688e6872184da9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736753"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="8ef06-102">ISymUnmanagedReader::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="8ef06-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="8ef06-103">初始化此读取器将与相关联，以及该模块的文件名称的元数据导入程序接口的符号读取器。</span><span class="sxs-lookup"><span data-stu-id="8ef06-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ef06-104">此方法可以将只调用一次，并必须读取器的任何其他方法之前调用。</span><span class="sxs-lookup"><span data-stu-id="8ef06-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef06-105">语法</span><span class="sxs-lookup"><span data-stu-id="8ef06-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef06-106">参数</span><span class="sxs-lookup"><span data-stu-id="8ef06-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="8ef06-107">[in]此读取器将与之关联的元数据导入程序接口。</span><span class="sxs-lookup"><span data-stu-id="8ef06-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="8ef06-108">[in]模块的文件名。</span><span class="sxs-lookup"><span data-stu-id="8ef06-108">[in] The file name of the module.</span></span> <span data-ttu-id="8ef06-109">可以使用`pIStream`参数相反。</span><span class="sxs-lookup"><span data-stu-id="8ef06-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="8ef06-110">[in]要搜索的路径。</span><span class="sxs-lookup"><span data-stu-id="8ef06-110">[in] The path to search.</span></span> <span data-ttu-id="8ef06-111">此参数可选。</span><span class="sxs-lookup"><span data-stu-id="8ef06-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="8ef06-112">[in]文件流用作 filename 参数的替代方法。</span><span class="sxs-lookup"><span data-stu-id="8ef06-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ef06-113">返回值</span><span class="sxs-lookup"><span data-stu-id="8ef06-113">Return Value</span></span>  
 <span data-ttu-id="8ef06-114">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="8ef06-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef06-115">备注</span><span class="sxs-lookup"><span data-stu-id="8ef06-115">Remarks</span></span>  
 <span data-ttu-id="8ef06-116">你需要仅指定一个`filename`或`pIStream`参数不可同时使用两者。</span><span class="sxs-lookup"><span data-stu-id="8ef06-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="8ef06-117">`searchPath` 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="8ef06-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef06-118">要求</span><span class="sxs-lookup"><span data-stu-id="8ef06-118">Requirements</span></span>  
 <span data-ttu-id="8ef06-119">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ef06-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef06-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="8ef06-120">See also</span></span>

- [<span data-ttu-id="8ef06-121">ISymUnmanagedReader 接口</span><span class="sxs-lookup"><span data-stu-id="8ef06-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
