---
title: ICorDebugModule2::ApplyChanges 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764338"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="09c7b-102">ICorDebugModule2::ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="09c7b-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="09c7b-103">适用于正在运行的进程中元数据的更改和 Microsoft 中间语言 (MSIL) 代码中的更改。</span><span class="sxs-lookup"><span data-stu-id="09c7b-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c7b-104">语法</span><span class="sxs-lookup"><span data-stu-id="09c7b-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09c7b-105">参数</span><span class="sxs-lookup"><span data-stu-id="09c7b-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="09c7b-106">[in]以字节为单位的增量元数据的大小。</span><span class="sxs-lookup"><span data-stu-id="09c7b-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="09c7b-107">[in]包含增量元数据的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="09c7b-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="09c7b-108">从返回的缓冲区的地址[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="09c7b-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="09c7b-109">元数据中的相对虚拟地址 (Rva) 应是 MSIL 代码开头的相对路径。</span><span class="sxs-lookup"><span data-stu-id="09c7b-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="09c7b-110">[in]大小，以字节为单位的增量 MSIL 代码。</span><span class="sxs-lookup"><span data-stu-id="09c7b-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="09c7b-111">[in]包含更新的 MSIL 代码的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="09c7b-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09c7b-112">备注</span><span class="sxs-lookup"><span data-stu-id="09c7b-112">Remarks</span></span>  
 <span data-ttu-id="09c7b-113">`pbMetadata`参数是特殊的增量元数据格式 (通过为输出[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。</span><span class="sxs-lookup"><span data-stu-id="09c7b-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="09c7b-114">`pbMetadata` 采用作为基的上一个元数据，描述要应用于此基本的单个更改。</span><span class="sxs-lookup"><span data-stu-id="09c7b-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="09c7b-115">与此相反， `pbIL[`] 参数包含的更新的方法的新 MSIL，并且应彻底替换该方法的上一个 MSIL</span><span class="sxs-lookup"><span data-stu-id="09c7b-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="09c7b-116">调试程序时在调试器的内存中已创建增量 MSIL 和元数据，调用`ApplyChanges`发送到公共语言运行时 (CLR) 的更改。</span><span class="sxs-lookup"><span data-stu-id="09c7b-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="09c7b-117">运行时更新其元数据的表、 将新的 MSIL 放入进程，并设置新的 MSIL 中实时 (JIT) 编译。</span><span class="sxs-lookup"><span data-stu-id="09c7b-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="09c7b-118">应用所做的更改后，应调用调试器[IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)准备的下一个编辑会话。</span><span class="sxs-lookup"><span data-stu-id="09c7b-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="09c7b-119">然后，调试器可能会继续执行过程。</span><span class="sxs-lookup"><span data-stu-id="09c7b-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="09c7b-120">每当调试器调用`ApplyChanges`对具有增量元数据的模块，它还应调用[imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)与在该模块的元数据除外复制其副本的所有相同的增量元数据用于发出所做的更改。</span><span class="sxs-lookup"><span data-stu-id="09c7b-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="09c7b-121">如果元数据的副本以某种方式将成为同步扩展使用的实际元数据，调试器可以始终丢弃该副本并获取新副本。</span><span class="sxs-lookup"><span data-stu-id="09c7b-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="09c7b-122">如果`ApplyChanges`方法失败，则调试会话处于无效状态，且必须重新启动。</span><span class="sxs-lookup"><span data-stu-id="09c7b-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09c7b-123">要求</span><span class="sxs-lookup"><span data-stu-id="09c7b-123">Requirements</span></span>  
 <span data-ttu-id="09c7b-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09c7b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09c7b-125">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09c7b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09c7b-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09c7b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09c7b-127">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09c7b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
