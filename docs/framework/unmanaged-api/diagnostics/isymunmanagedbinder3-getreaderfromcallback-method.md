---
title: ISymUnmanagedBinder3::GetReaderFromCallback 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed0097e072b34dd43876ddf23abbc1f513670ff
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776815"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="b720a-102">ISymUnmanagedBinder3::GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="b720a-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="b720a-103">允许用户实现或通过回调提供`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`从内存中获取的调试目录信息。</span><span class="sxs-lookup"><span data-stu-id="b720a-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b720a-104">语法</span><span class="sxs-lookup"><span data-stu-id="b720a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b720a-105">参数</span><span class="sxs-lookup"><span data-stu-id="b720a-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="b720a-106">[in]指向元数据导入接口的指针。</span><span class="sxs-lookup"><span data-stu-id="b720a-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b720a-107">[in]一个指向的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b720a-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b720a-108">[in]搜索路径指向的指针。</span><span class="sxs-lookup"><span data-stu-id="b720a-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="b720a-109">[in]值为[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)枚举，用于指定要执行的符号读取器的搜索时使用的策略。</span><span class="sxs-lookup"><span data-stu-id="b720a-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="b720a-110">[in]指向回调函数的指针。</span><span class="sxs-lookup"><span data-stu-id="b720a-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b720a-111">[out]一个指针，它设置为返回[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="b720a-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b720a-112">返回值</span><span class="sxs-lookup"><span data-stu-id="b720a-112">Return Value</span></span>  
 <span data-ttu-id="b720a-113">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="b720a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b720a-114">要求</span><span class="sxs-lookup"><span data-stu-id="b720a-114">Requirements</span></span>  
 <span data-ttu-id="b720a-115">**标头：** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="b720a-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b720a-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="b720a-116">See also</span></span>

- [<span data-ttu-id="b720a-117">ISymUnmanagedBinder3 接口</span><span class="sxs-lookup"><span data-stu-id="b720a-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
