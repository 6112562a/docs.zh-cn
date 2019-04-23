---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153317"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="840a0-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="840a0-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="840a0-103">[支持版本：[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 及更高版本]</span><span class="sxs-lookup"><span data-stu-id="840a0-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="840a0-104">从内存中的符号流读取字节数。</span><span class="sxs-lookup"><span data-stu-id="840a0-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840a0-105">语法</span><span class="sxs-lookup"><span data-stu-id="840a0-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="840a0-106">参数</span><span class="sxs-lookup"><span data-stu-id="840a0-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="840a0-107">[in]包含内存中流的模块标识符。</span><span class="sxs-lookup"><span data-stu-id="840a0-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="840a0-108">[in]在开始读取字节的内存中流内的偏移量。</span><span class="sxs-lookup"><span data-stu-id="840a0-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="840a0-109">[out]指向数据将复制到其中的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="840a0-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="840a0-110">缓冲区应具有`countSymbolBytes`的可用空间。</span><span class="sxs-lookup"><span data-stu-id="840a0-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="840a0-111">[in]要复制的字节数。</span><span class="sxs-lookup"><span data-stu-id="840a0-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="840a0-112">[out]方法返回时，包含实际读取的字节数。</span><span class="sxs-lookup"><span data-stu-id="840a0-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="840a0-113">返回值</span><span class="sxs-lookup"><span data-stu-id="840a0-113">Return Value</span></span>  
 <span data-ttu-id="840a0-114">`S_OK`如果已读取的字节非零值数。</span><span class="sxs-lookup"><span data-stu-id="840a0-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="840a0-115">`CORPROF_E_MODULE_IS_DYNAMIC`如果该模块使用创建<xref:System.Reflection.Emit>。</span><span class="sxs-lookup"><span data-stu-id="840a0-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="840a0-116">备注</span><span class="sxs-lookup"><span data-stu-id="840a0-116">Remarks</span></span>  
 <span data-ttu-id="840a0-117">`ReadInMemorySymbols`方法会尝试读取`countSymbolBytes`的数据偏移量开始`symbolsReadOffset`中内存流中。</span><span class="sxs-lookup"><span data-stu-id="840a0-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="840a0-118">将数据复制到`pSymbolBytes`，这都必须具有`countSymbolBytes`的可用空间。</span><span class="sxs-lookup"><span data-stu-id="840a0-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="840a0-119">`pCountSymbolsBytesRead` 包含实际读取，这可能会更少的字节数比`countSymbolBytes`如果到达流的末尾。</span><span class="sxs-lookup"><span data-stu-id="840a0-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="840a0-120">当前实现不支持 Reflection.Emit。</span><span class="sxs-lookup"><span data-stu-id="840a0-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="840a0-121">如果通过使用 Reflection.Emit 创建模块，该方法返回`CORPROF_E_MODULE_IS_DYNAMIC`。</span><span class="sxs-lookup"><span data-stu-id="840a0-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="840a0-122">要求</span><span class="sxs-lookup"><span data-stu-id="840a0-122">Requirements</span></span>  
 <span data-ttu-id="840a0-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="840a0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="840a0-124">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="840a0-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="840a0-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="840a0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="840a0-126">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="840a0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840a0-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="840a0-127">See also</span></span>

- [<span data-ttu-id="840a0-128">ICorProfilerInfo7 接口</span><span class="sxs-lookup"><span data-stu-id="840a0-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
