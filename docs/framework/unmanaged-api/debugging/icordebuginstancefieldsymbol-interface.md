---
title: ICorDebugInstanceFieldSymbol 接口
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 2ed1d70f554ca0a4a49639fe53a2ddbb0497c0a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122732"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="49eab-102">ICorDebugInstanceFieldSymbol 接口</span><span class="sxs-lookup"><span data-stu-id="49eab-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="49eab-103">表示某一实例字段的调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="49eab-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49eab-104">方法</span><span class="sxs-lookup"><span data-stu-id="49eab-104">Methods</span></span>  
  
|<span data-ttu-id="49eab-105">方法</span><span class="sxs-lookup"><span data-stu-id="49eab-105">Method</span></span>|<span data-ttu-id="49eab-106">描述</span><span class="sxs-lookup"><span data-stu-id="49eab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49eab-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="49eab-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="49eab-108">获取实例字段的名称。</span><span class="sxs-lookup"><span data-stu-id="49eab-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="49eab-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="49eab-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="49eab-110">获取父类中此示例字段的偏移量（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="49eab-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="49eab-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="49eab-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="49eab-112">获取实例字段的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="49eab-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49eab-113">备注</span><span class="sxs-lookup"><span data-stu-id="49eab-113">Remarks</span></span>  
 <span data-ttu-id="49eab-114">`ICorDebugInstanceFieldSymbol` 接口用于检索实例字段的调试符号信息。</span><span class="sxs-lookup"><span data-stu-id="49eab-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49eab-115">此接口仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="49eab-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="49eab-116">如果在 .NET Native 外为 ICorDebug 方案实现此接口，则公共语言运行时将忽略此接口。</span><span class="sxs-lookup"><span data-stu-id="49eab-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49eab-117">要求</span><span class="sxs-lookup"><span data-stu-id="49eab-117">Requirements</span></span>  
 <span data-ttu-id="49eab-118">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49eab-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49eab-119">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49eab-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49eab-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49eab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49eab-121">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49eab-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49eab-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="49eab-122">See also</span></span>

- [<span data-ttu-id="49eab-123">ICorDebugStaticFieldSymbol 接口</span><span class="sxs-lookup"><span data-stu-id="49eab-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="49eab-124">调试接口</span><span class="sxs-lookup"><span data-stu-id="49eab-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="49eab-125">调试</span><span class="sxs-lookup"><span data-stu-id="49eab-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
