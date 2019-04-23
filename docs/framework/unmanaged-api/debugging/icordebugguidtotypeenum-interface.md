---
title: ICorDebugGuidToTypeEnum 接口
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210654"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="0559b-102">ICorDebugGuidToTypeEnum 接口</span><span class="sxs-lookup"><span data-stu-id="0559b-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="0559b-103">提供定义的 Guid 的一组与由 ICorDebugType 实例来表示其相应类型之间的映射的枚举器。</span><span class="sxs-lookup"><span data-stu-id="0559b-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="0559b-104">此接口继承自 ICorDebugEnum 接口的方法。</span><span class="sxs-lookup"><span data-stu-id="0559b-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0559b-105">方法</span><span class="sxs-lookup"><span data-stu-id="0559b-105">Methods</span></span>  
  
|<span data-ttu-id="0559b-106">方法</span><span class="sxs-lookup"><span data-stu-id="0559b-106">Method</span></span>|<span data-ttu-id="0559b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0559b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0559b-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="0559b-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="0559b-109">获取指定的数目的[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)映射 Guid 类型信息的实例。</span><span class="sxs-lookup"><span data-stu-id="0559b-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0559b-110">备注</span><span class="sxs-lookup"><span data-stu-id="0559b-110">Remarks</span></span>  
 <span data-ttu-id="0559b-111">`ICorDebugGuidToTypeEnum`接口对象可以通过调用来检索[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0559b-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="0559b-112">调试程序可以调用此接口[下一步](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)方法来检索[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)表示的映射的对象进行管理的表示形式[!INCLUDE[wrt](../../../../includes/wrt-md.md)]中加载类型使用为调用应用程序域[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0559b-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0559b-113">要求</span><span class="sxs-lookup"><span data-stu-id="0559b-113">Requirements</span></span>  
 <span data-ttu-id="0559b-114">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0559b-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="0559b-115">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0559b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0559b-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0559b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0559b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0559b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0559b-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="0559b-118">See also</span></span>

- [<span data-ttu-id="0559b-119">调试接口</span><span class="sxs-lookup"><span data-stu-id="0559b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
