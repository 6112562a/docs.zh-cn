---
title: “Cor调试代码调用类型”枚举
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eeb8aba318d53efbc699d4492a86b2667bcfff
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274123"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="5b291-102">“Cor调试代码调用类型”枚举</span><span class="sxs-lookup"><span data-stu-id="5b291-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="5b291-103">描述导出函数如何调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="5b291-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b291-104">语法</span><span class="sxs-lookup"><span data-stu-id="5b291-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="5b291-105">成员</span><span class="sxs-lookup"><span data-stu-id="5b291-105">Members</span></span>  
  
|<span data-ttu-id="5b291-106">成员</span><span class="sxs-lookup"><span data-stu-id="5b291-106">Member</span></span>|<span data-ttu-id="5b291-107">描述</span><span class="sxs-lookup"><span data-stu-id="5b291-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="5b291-108">如果任何托管代码遭该方法调用，稍后将必须接受显式事件或断点定位。</span><span class="sxs-lookup"><span data-stu-id="5b291-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="5b291-109">--或者--</span><span class="sxs-lookup"><span data-stu-id="5b291-109">--or--</span></span><br /><br /> <span data-ttu-id="5b291-110">我们或许只能错过该方法调用的一些托管代码，因为很难停在上面。</span><span class="sxs-lookup"><span data-stu-id="5b291-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="5b291-111">--或者--</span><span class="sxs-lookup"><span data-stu-id="5b291-111">--or--</span></span><br /><br /> <span data-ttu-id="5b291-112">该方法可能无法调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="5b291-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="5b291-113">该方法可通过返回指令调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="5b291-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="5b291-114">在下一个托管代码处应跳出。</span><span class="sxs-lookup"><span data-stu-id="5b291-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="5b291-115">该方法可通过尾调调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="5b291-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="5b291-116">在托管代码处应单步执行所有调用指令。</span><span class="sxs-lookup"><span data-stu-id="5b291-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b291-117">备注</span><span class="sxs-lookup"><span data-stu-id="5b291-117">Remarks</span></span>  
 <span data-ttu-id="5b291-118">此枚举由[ICorDebugProcess6：： GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md)方法用来提供有关单步执行托管代码的信息。</span><span class="sxs-lookup"><span data-stu-id="5b291-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b291-119">此枚举仅用于 .NET Native 调试方案。</span><span class="sxs-lookup"><span data-stu-id="5b291-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b291-120">要求</span><span class="sxs-lookup"><span data-stu-id="5b291-120">Requirements</span></span>  
 <span data-ttu-id="5b291-121">**适用**请参阅[系统需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b291-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b291-122">**标头：** Cordebug.idl，Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="5b291-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b291-123">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b291-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b291-124">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b291-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b291-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b291-125">See also</span></span>

- [<span data-ttu-id="5b291-126">调试枚举</span><span class="sxs-lookup"><span data-stu-id="5b291-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5b291-127">调试</span><span class="sxs-lookup"><span data-stu-id="5b291-127">Debugging</span></span>](index.md)
