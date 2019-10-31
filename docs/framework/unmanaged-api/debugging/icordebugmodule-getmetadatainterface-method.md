---
title: ICorDebugModule::GetMetaDataInterface 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129552"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="41c0d-102">ICorDebugModule::GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="41c0d-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="41c0d-103">获取可用于检查模块的元数据的元数据接口对象。</span><span class="sxs-lookup"><span data-stu-id="41c0d-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c0d-104">语法</span><span class="sxs-lookup"><span data-stu-id="41c0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41c0d-105">参数</span><span class="sxs-lookup"><span data-stu-id="41c0d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="41c0d-106">中用于指定元数据接口的引用 ID。</span><span class="sxs-lookup"><span data-stu-id="41c0d-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="41c0d-107">弄一个指针，指向作为[元数据接口](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)之一的 `T:IUnknown` 对象的地址。</span><span class="sxs-lookup"><span data-stu-id="41c0d-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41c0d-108">备注</span><span class="sxs-lookup"><span data-stu-id="41c0d-108">Remarks</span></span>  
 <span data-ttu-id="41c0d-109">调试器可以使用 `GetMetaDataInterface` 方法创建模块的原始元数据的副本，必须执行此操作才能编辑该模块。</span><span class="sxs-lookup"><span data-stu-id="41c0d-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="41c0d-110">调试器调用 `GetMetaDataInterface` 获取该模块的[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)接口对象，然后调用[IMetaDataEmit：： SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)将模块的元数据副本保存到内存。</span><span class="sxs-lookup"><span data-stu-id="41c0d-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c0d-111">要求</span><span class="sxs-lookup"><span data-stu-id="41c0d-111">Requirements</span></span>  
 <span data-ttu-id="41c0d-112">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41c0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c0d-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41c0d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41c0d-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41c0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c0d-115">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c0d-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="41c0d-116">See also</span></span>

- [<span data-ttu-id="41c0d-117">元数据</span><span class="sxs-lookup"><span data-stu-id="41c0d-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
