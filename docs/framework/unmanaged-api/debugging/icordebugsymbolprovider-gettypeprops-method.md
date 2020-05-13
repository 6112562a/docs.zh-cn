---
title: ICorDebugSymbolProvider::GetTypeProps 方法
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: e116716284bb2081edb669e7fc9083cde10f6457
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379364"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="b1766-102">ICorDebugSymbolProvider::GetTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="b1766-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="b1766-103">给定 vtable 中的相对虚拟地址 (RVA)，返回类型的属性信息（例如其泛型参数的签名数量）。</span><span class="sxs-lookup"><span data-stu-id="b1766-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1766-104">语法</span><span class="sxs-lookup"><span data-stu-id="b1766-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1766-105">参数</span><span class="sxs-lookup"><span data-stu-id="b1766-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="b1766-106">[in] vtable 中的相对虚拟地址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="b1766-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="b1766-107">[in] `signature` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="b1766-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="b1766-108">请参阅“备注”部分。</span><span class="sxs-lookup"><span data-stu-id="b1766-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="b1766-109">[out] [out] 指向返回的 `signature` 数组的大小的指针。</span><span class="sxs-lookup"><span data-stu-id="b1766-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="b1766-110">[out] 保存所有泛型参数的 typespec 签名的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="b1766-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1766-111">备注</span><span class="sxs-lookup"><span data-stu-id="b1766-111">Remarks</span></span>  
 <span data-ttu-id="b1766-112">若要获取类型的数组的所需大小 `signature` ，请将 `cbSignature` 参数设置为0，将设置 `signature` 为**null**。</span><span class="sxs-lookup"><span data-stu-id="b1766-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="b1766-113">当该方法返回时，`pcbSignature` 将包含 `signature` 数组所需的字节数。</span><span class="sxs-lookup"><span data-stu-id="b1766-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1766-114">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="b1766-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1766-115">要求</span><span class="sxs-lookup"><span data-stu-id="b1766-115">Requirements</span></span>  
 <span data-ttu-id="b1766-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1766-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1766-117">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1766-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1766-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1766-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1766-119">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1766-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1766-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1766-120">See also</span></span>

- [<span data-ttu-id="b1766-121">GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="b1766-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="b1766-122">ICorDebugSymbolProvider 接口</span><span class="sxs-lookup"><span data-stu-id="b1766-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b1766-123">调试接口</span><span class="sxs-lookup"><span data-stu-id="b1766-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
