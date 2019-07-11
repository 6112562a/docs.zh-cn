---
title: ICorDebugProcess5::GetTypeLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee556f559a7dc4c271f110f7bba4c86b675c3511
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736490"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="25833-102">ICorDebugProcess5::GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="25833-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="25833-103">获取基于其类型标识符的内存中对象的布局信息。</span><span class="sxs-lookup"><span data-stu-id="25833-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25833-104">语法</span><span class="sxs-lookup"><span data-stu-id="25833-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25833-105">参数</span><span class="sxs-lookup"><span data-stu-id="25833-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="25833-106">[in]一个[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)标记，用于指定需要其布局的类型。</span><span class="sxs-lookup"><span data-stu-id="25833-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="25833-107">[out]一个指向[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)结构，其中包含在内存中对象的布局信息。</span><span class="sxs-lookup"><span data-stu-id="25833-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25833-108">备注</span><span class="sxs-lookup"><span data-stu-id="25833-108">Remarks</span></span>  
 <span data-ttu-id="25833-109">`ICorDebugProcess5::GetTypeLayout`方法提供基于对象有关的信息及其[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，返回由其他许多[ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="25833-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="25833-110">提供的信息[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)方法填充的结构。</span><span class="sxs-lookup"><span data-stu-id="25833-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25833-111">要求</span><span class="sxs-lookup"><span data-stu-id="25833-111">Requirements</span></span>  
 <span data-ttu-id="25833-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25833-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25833-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25833-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25833-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25833-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25833-115">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25833-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25833-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="25833-116">See also</span></span>

- [<span data-ttu-id="25833-117">COR_TYPE_LAYOUT 结构</span><span class="sxs-lookup"><span data-stu-id="25833-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [<span data-ttu-id="25833-118">ICorDebugProcess5 接口</span><span class="sxs-lookup"><span data-stu-id="25833-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="25833-119">调试接口</span><span class="sxs-lookup"><span data-stu-id="25833-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
