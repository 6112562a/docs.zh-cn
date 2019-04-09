---
title: ICorDebugModule2 接口
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3fb1bf3f61c78f4eb157b93363b1c06b25bee04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119894"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="75c48-102">ICorDebugModule2 接口</span><span class="sxs-lookup"><span data-stu-id="75c48-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="75c48-103">用作 icor 调试模块接口的逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="75c48-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75c48-104">方法</span><span class="sxs-lookup"><span data-stu-id="75c48-104">Methods</span></span>  
  
|<span data-ttu-id="75c48-105">方法</span><span class="sxs-lookup"><span data-stu-id="75c48-105">Method</span></span>|<span data-ttu-id="75c48-106">描述</span><span class="sxs-lookup"><span data-stu-id="75c48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75c48-107">ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="75c48-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="75c48-108">适用于正在运行的进程中元数据的更改和 Microsoft 中间语言 (MSIL) 代码中的更改。</span><span class="sxs-lookup"><span data-stu-id="75c48-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="75c48-109">GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="75c48-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="75c48-110">获取用于控制实时 (JIT) 编译的标志`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="75c48-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="75c48-111">ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="75c48-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="75c48-112">解析指定的元数据标记所引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="75c48-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="75c48-113">SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="75c48-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="75c48-114">设置用于控制此 JIT 编译的标志`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="75c48-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="75c48-115">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="75c48-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="75c48-116">在此设置的所有类的所有方法只是我的代码 (JMC) 状态`ICorDebugModule2`为指定的值，除中`pTokens`数组，它将设置为相反值。</span><span class="sxs-lookup"><span data-stu-id="75c48-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75c48-117">备注</span><span class="sxs-lookup"><span data-stu-id="75c48-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75c48-118">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="75c48-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c48-119">要求</span><span class="sxs-lookup"><span data-stu-id="75c48-119">Requirements</span></span>  
 <span data-ttu-id="75c48-120">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75c48-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75c48-121">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75c48-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75c48-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75c48-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="75c48-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="75c48-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75c48-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="75c48-124">See also</span></span>

- [<span data-ttu-id="75c48-125">调试接口</span><span class="sxs-lookup"><span data-stu-id="75c48-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
