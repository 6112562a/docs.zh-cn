---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 35767529d9433764b7eed0b3b4acdd806f399962
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792185"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="eb5f0-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="eb5f0-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="eb5f0-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="eb5f0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eb5f0-104">配置调试器如何处理目标进程中元数据的内存中更新。</span><span class="sxs-lookup"><span data-stu-id="eb5f0-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb5f0-105">语法</span><span class="sxs-lookup"><span data-stu-id="eb5f0-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb5f0-106">参数</span><span class="sxs-lookup"><span data-stu-id="eb5f0-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="eb5f0-107">一个[WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)枚举值，该值指定目标进程中的元数据的内存中更新是否可见（`WriteableMetadataUpdateMode::AlwaysShowUpdates`）或不显示（`WriteableMetadataUpdateMode::LegacyCompatPolicy`）到调试器。</span><span class="sxs-lookup"><span data-stu-id="eb5f0-107">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb5f0-108">备注</span><span class="sxs-lookup"><span data-stu-id="eb5f0-108">Remarks</span></span>  
 <span data-ttu-id="eb5f0-109">目标进程中元数据的更新可以来自于“编辑并继续”、探查器或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="eb5f0-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb5f0-110">需求</span><span class="sxs-lookup"><span data-stu-id="eb5f0-110">Requirements</span></span>  
 <span data-ttu-id="eb5f0-111">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb5f0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb5f0-112">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb5f0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb5f0-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb5f0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb5f0-114">**.NET Framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb5f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb5f0-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb5f0-115">See also</span></span>

- [<span data-ttu-id="eb5f0-116">ICorDebugProcess7 接口</span><span class="sxs-lookup"><span data-stu-id="eb5f0-116">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="eb5f0-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="eb5f0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
