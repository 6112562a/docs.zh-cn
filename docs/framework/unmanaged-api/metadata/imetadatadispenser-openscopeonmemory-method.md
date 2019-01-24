---
title: IMetaDataDispenser::OpenScopeOnMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6233e5ecb479db43f35c9d95c42c66c02c81122f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648925"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="6071a-102">IMetaDataDispenser::OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="6071a-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="6071a-103">将打开一个包含现有的元数据的内存区域。</span><span class="sxs-lookup"><span data-stu-id="6071a-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="6071a-104">也就是说，此方法打开现有数据视为元数据的内存的指定的区域。</span><span class="sxs-lookup"><span data-stu-id="6071a-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6071a-105">语法</span><span class="sxs-lookup"><span data-stu-id="6071a-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6071a-106">参数</span><span class="sxs-lookup"><span data-stu-id="6071a-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="6071a-107">[in]指定的内存区域的起始地址的指针。</span><span class="sxs-lookup"><span data-stu-id="6071a-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="6071a-108">[in]内存区域中，以字节为单位的大小。</span><span class="sxs-lookup"><span data-stu-id="6071a-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6071a-109">[in]值为[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚举，用于打开指定的模式 （读取、 写入和其他操作）。</span><span class="sxs-lookup"><span data-stu-id="6071a-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="6071a-110">[in]要返回; 所需的元数据接口的 IID调用方将使用该接口导入 （读取） 或发出 （写入） 元数据。</span><span class="sxs-lookup"><span data-stu-id="6071a-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="6071a-111">值`riid`必须指定一个"导入"发出"接口。</span><span class="sxs-lookup"><span data-stu-id="6071a-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="6071a-112">有效值为 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="6071a-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6071a-113">[out]对返回的接口指针。</span><span class="sxs-lookup"><span data-stu-id="6071a-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6071a-114">备注</span><span class="sxs-lookup"><span data-stu-id="6071a-114">Remarks</span></span>  
 <span data-ttu-id="6071a-115">方法使用从一个"导入"接口，或添加到使用从"发出"界面中的一个方法，可以查询的元数据的内存中副本。</span><span class="sxs-lookup"><span data-stu-id="6071a-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="6071a-116">`OpenScopeOnMemory`方法是类似于[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，只不过在内存中，而不是在磁盘上的文件已存在所需的元数据。</span><span class="sxs-lookup"><span data-stu-id="6071a-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="6071a-117">如果内存的目标区域不包含公共语言运行时 (CLR) 元数据、`OpenScopeOnMemory`方法将失败。</span><span class="sxs-lookup"><span data-stu-id="6071a-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6071a-118">要求</span><span class="sxs-lookup"><span data-stu-id="6071a-118">Requirements</span></span>  
 <span data-ttu-id="6071a-119">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6071a-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6071a-120">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6071a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6071a-121">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6071a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6071a-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6071a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6071a-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="6071a-123">See also</span></span>
- [<span data-ttu-id="6071a-124">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="6071a-125">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="6071a-126">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="6071a-127">IMetaDataAssemblyImport 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6071a-128">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="6071a-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6071a-129">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="6071a-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="6071a-130">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6071a-131">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="6071a-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
