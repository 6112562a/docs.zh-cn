---
title: ISymUnmanagedWriter::DefineField 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37794d40b4b379c5d3a05935cf1f2b7b3da11baa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777363"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="f3717-102">ISymUnmanagedWriter::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="f3717-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="f3717-103">定义一个不在方法内的变量。</span><span class="sxs-lookup"><span data-stu-id="f3717-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="f3717-104">此方法是使用类中的某些字段、 位域等。</span><span class="sxs-lookup"><span data-stu-id="f3717-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3717-105">语法</span><span class="sxs-lookup"><span data-stu-id="f3717-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3717-106">参数</span><span class="sxs-lookup"><span data-stu-id="f3717-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="f3717-107">[in]元数据类型或方法令牌。</span><span class="sxs-lookup"><span data-stu-id="f3717-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="f3717-108">[in]字段名称。</span><span class="sxs-lookup"><span data-stu-id="f3717-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f3717-109">[in]字段特性。</span><span class="sxs-lookup"><span data-stu-id="f3717-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="f3717-110">[in]一个`ULONG32`，它是大小，以字符为单位，包含字段签名所需的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f3717-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="f3717-111">[in]字段签名的数组。</span><span class="sxs-lookup"><span data-stu-id="f3717-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f3717-112">[in]地址类型。</span><span class="sxs-lookup"><span data-stu-id="f3717-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f3717-113">[in]字段规格的第一个地址。</span><span class="sxs-lookup"><span data-stu-id="f3717-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f3717-114">[in]字段规格的第二个地址。</span><span class="sxs-lookup"><span data-stu-id="f3717-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f3717-115">[in]字段规格的第三个地址。</span><span class="sxs-lookup"><span data-stu-id="f3717-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3717-116">返回值</span><span class="sxs-lookup"><span data-stu-id="f3717-116">Return Value</span></span>  
 <span data-ttu-id="f3717-117">如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="f3717-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3717-118">要求</span><span class="sxs-lookup"><span data-stu-id="f3717-118">Requirements</span></span>  
 <span data-ttu-id="f3717-119">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3717-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3717-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3717-120">See also</span></span>

- [<span data-ttu-id="f3717-121">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="f3717-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
