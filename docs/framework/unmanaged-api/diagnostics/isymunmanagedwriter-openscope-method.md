---
title: ISymUnmanagedWriter::OpenScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6d563873045b4b5b427f06f0caa5420d31590b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777211"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="6eee0-102">ISymUnmanagedWriter::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="6eee0-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="6eee0-103">在当前方法中打开新的词法范围。</span><span class="sxs-lookup"><span data-stu-id="6eee0-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="6eee0-104">范围将成为新的当前作用域，并推送到的作用域堆栈上。</span><span class="sxs-lookup"><span data-stu-id="6eee0-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="6eee0-105">作用域必须形成层次结构。</span><span class="sxs-lookup"><span data-stu-id="6eee0-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="6eee0-106">同级不能重叠。</span><span class="sxs-lookup"><span data-stu-id="6eee0-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eee0-107">语法</span><span class="sxs-lookup"><span data-stu-id="6eee0-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eee0-108">参数</span><span class="sxs-lookup"><span data-stu-id="6eee0-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="6eee0-109">[in]在词法范围内，以字节为单位，从该方法开头的第一个指令的偏移量。</span><span class="sxs-lookup"><span data-stu-id="6eee0-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6eee0-110">[out]一个指向`ULONG32`接收范围标识符。</span><span class="sxs-lookup"><span data-stu-id="6eee0-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eee0-111">返回值</span><span class="sxs-lookup"><span data-stu-id="6eee0-111">Return Value</span></span>  
 <span data-ttu-id="6eee0-112">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="6eee0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eee0-113">备注</span><span class="sxs-lookup"><span data-stu-id="6eee0-113">Remarks</span></span>  
 <span data-ttu-id="6eee0-114">`ISymUnmanagedWriter::OpenScope` 返回可用于不透明的范围标识符[isymunmanagedwriter:: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)来定义范围的起始和结束偏移量在更高版本时。</span><span class="sxs-lookup"><span data-stu-id="6eee0-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="6eee0-115">在这种情况下，偏移量传递给`ISymUnmanagedWriter::OpenScope`并[isymunmanagedwriter:: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)将被忽略。</span><span class="sxs-lookup"><span data-stu-id="6eee0-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="6eee0-116">范围标识符是仅在当前方法中有效。</span><span class="sxs-lookup"><span data-stu-id="6eee0-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eee0-117">要求</span><span class="sxs-lookup"><span data-stu-id="6eee0-117">Requirements</span></span>  
 <span data-ttu-id="6eee0-118">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6eee0-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eee0-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="6eee0-119">See also</span></span>

- [<span data-ttu-id="6eee0-120">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="6eee0-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
