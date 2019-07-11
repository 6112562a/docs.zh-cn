---
title: ISymUnmanagedVariable::GetAddressField2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463416165d2dbd7724d5cf0d29e40d8243ade34b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778315"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="26d1d-102">ISymUnmanagedVariable::GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="26d1d-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="26d1d-103">获取此变量的第二个地址字段。</span><span class="sxs-lookup"><span data-stu-id="26d1d-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="26d1d-104">其含义取决于类型的地址。</span><span class="sxs-lookup"><span data-stu-id="26d1d-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d1d-105">语法</span><span class="sxs-lookup"><span data-stu-id="26d1d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d1d-106">参数</span><span class="sxs-lookup"><span data-stu-id="26d1d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="26d1d-107">[out]一个指向`ULONG32`接收第二个地址字段。</span><span class="sxs-lookup"><span data-stu-id="26d1d-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26d1d-108">返回值</span><span class="sxs-lookup"><span data-stu-id="26d1d-108">Return Value</span></span>  
 <span data-ttu-id="26d1d-109">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="26d1d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d1d-110">要求</span><span class="sxs-lookup"><span data-stu-id="26d1d-110">Requirements</span></span>  
 <span data-ttu-id="26d1d-111">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="26d1d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d1d-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="26d1d-112">See also</span></span>

- [<span data-ttu-id="26d1d-113">ISymUnmanagedVariable 接口</span><span class="sxs-lookup"><span data-stu-id="26d1d-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="26d1d-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="26d1d-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="26d1d-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="26d1d-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="26d1d-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="26d1d-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
