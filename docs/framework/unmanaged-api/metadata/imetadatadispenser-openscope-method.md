---
title: IMetaDataDispenser::OpenScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4ffbd2bc3042f7e37e90dceeb28ec50b3c73cef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491966"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="09a54-102">IMetaDataDispenser::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="09a54-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="09a54-103">打开一个现有的磁盘上的文件并将其元数据映射到内存中。</span><span class="sxs-lookup"><span data-stu-id="09a54-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a54-104">语法</span><span class="sxs-lookup"><span data-stu-id="09a54-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09a54-105">参数</span><span class="sxs-lookup"><span data-stu-id="09a54-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="09a54-106">[in]要打开的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="09a54-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="09a54-107">该文件必须包含公共语言运行时 (CLR) 元数据。</span><span class="sxs-lookup"><span data-stu-id="09a54-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="09a54-108">[in]值为[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚举，用于打开指定的模式 （读取、 写入和其他操作）。</span><span class="sxs-lookup"><span data-stu-id="09a54-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="09a54-109">[in]要返回; 所需的元数据接口的 IID调用方将使用该接口导入 （读取） 或发出 （写入） 元数据。</span><span class="sxs-lookup"><span data-stu-id="09a54-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="09a54-110">值`riid`必须指定一个"导入"发出"接口。</span><span class="sxs-lookup"><span data-stu-id="09a54-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="09a54-111">有效值为 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="09a54-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="09a54-112">[out]对返回的接口指针。</span><span class="sxs-lookup"><span data-stu-id="09a54-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a54-113">备注</span><span class="sxs-lookup"><span data-stu-id="09a54-113">Remarks</span></span>  
 <span data-ttu-id="09a54-114">方法使用从一个"导入"接口，或添加到使用从"发出"界面中的一个方法，可以查询的元数据的内存中副本。</span><span class="sxs-lookup"><span data-stu-id="09a54-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="09a54-115">如果目标文件不包含 CLR 元数据，`OpenScope`方法将失败。</span><span class="sxs-lookup"><span data-stu-id="09a54-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="09a54-116">在.NET Framework 版本 1.0 和 1.1 版中，如果作用域以打开`dwOpenFlags`设置为 ofRead，有资格享受共享。</span><span class="sxs-lookup"><span data-stu-id="09a54-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="09a54-117">也就是说，如果后续调用`OpenScope`传入以前打开的文件的名称，重用现有的范围，且不会创建一组新的数据结构。</span><span class="sxs-lookup"><span data-stu-id="09a54-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="09a54-118">但是，由于这种共享会出现问题。</span><span class="sxs-lookup"><span data-stu-id="09a54-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="09a54-119">在.NET Framework 2.0 版中，作用域以打开`dwOpenFlags`不再共享设置为 ofRead。</span><span class="sxs-lookup"><span data-stu-id="09a54-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="09a54-120">使用 ofReadOnly 值以允许要共享的作用域。</span><span class="sxs-lookup"><span data-stu-id="09a54-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="09a54-121">共享作用域后，使用"读/写"元数据接口的查询将失败。</span><span class="sxs-lookup"><span data-stu-id="09a54-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a54-122">要求</span><span class="sxs-lookup"><span data-stu-id="09a54-122">Requirements</span></span>  
 <span data-ttu-id="09a54-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09a54-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a54-124">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09a54-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09a54-125">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="09a54-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09a54-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a54-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a54-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="09a54-127">See also</span></span>
- [<span data-ttu-id="09a54-128">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="09a54-129">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="09a54-130">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="09a54-131">IMetaDataAssemblyImport 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="09a54-132">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="09a54-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="09a54-133">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="09a54-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="09a54-134">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="09a54-135">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="09a54-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
