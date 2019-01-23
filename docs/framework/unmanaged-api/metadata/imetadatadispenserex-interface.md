---
title: IMetaDataDispenserEx 接口
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4fa4830756ee6ac896611dbc243207739151d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547314"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="74cbb-102">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="74cbb-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="74cbb-103">扩展了[IMetaDataDispenser 接口](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)接口，以提供的功能来控制对当前元数据范围的元数据 Api 的进行操作。</span><span class="sxs-lookup"><span data-stu-id="74cbb-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74cbb-104">方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-104">Methods</span></span>  
  
|<span data-ttu-id="74cbb-105">方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-105">Method</span></span>|<span data-ttu-id="74cbb-106">描述</span><span class="sxs-lookup"><span data-stu-id="74cbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74cbb-107">FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="74cbb-108">未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="74cbb-108">This method is not implemented.</span></span> <span data-ttu-id="74cbb-109">如果调用，则返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="74cbb-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="74cbb-110">FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="74cbb-111">未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="74cbb-111">This method is not implemented.</span></span> <span data-ttu-id="74cbb-112">如果调用，则返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="74cbb-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="74cbb-113">GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="74cbb-114">获取包含当前的公共语言运行时 (CLR) 的目录。</span><span class="sxs-lookup"><span data-stu-id="74cbb-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="74cbb-115">进程外调试器支持此方法仅供使用。</span><span class="sxs-lookup"><span data-stu-id="74cbb-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="74cbb-116">如果从另一个组件调用，它将返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="74cbb-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="74cbb-117">GetOption 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="74cbb-118">获取当前元数据范围的指定选项的值。</span><span class="sxs-lookup"><span data-stu-id="74cbb-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="74cbb-119">选项，可以控制如何处理对当前元数据范围的调用。</span><span class="sxs-lookup"><span data-stu-id="74cbb-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="74cbb-120">OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="74cbb-121">未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="74cbb-121">This method is not implemented.</span></span> <span data-ttu-id="74cbb-122">如果调用，则返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="74cbb-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="74cbb-123">SetOption 方法</span><span class="sxs-lookup"><span data-stu-id="74cbb-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="74cbb-124">将指定的选项设置为当前元数据范围的给定值。</span><span class="sxs-lookup"><span data-stu-id="74cbb-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="74cbb-125">选项，可以控制如何处理对当前元数据范围的调用。</span><span class="sxs-lookup"><span data-stu-id="74cbb-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74cbb-126">要求</span><span class="sxs-lookup"><span data-stu-id="74cbb-126">Requirements</span></span>  
 <span data-ttu-id="74cbb-127">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74cbb-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74cbb-128">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74cbb-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74cbb-129">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="74cbb-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74cbb-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74cbb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74cbb-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="74cbb-131">See also</span></span>
- [<span data-ttu-id="74cbb-132">元数据接口</span><span class="sxs-lookup"><span data-stu-id="74cbb-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="74cbb-133">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="74cbb-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="74cbb-134">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="74cbb-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="74cbb-135">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="74cbb-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
