---
title: IMetaDataEmit::GetSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777387"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="a35f7-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="a35f7-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="a35f7-103">获取当前作用域中的程序集和其元数据的估计二进制大小。</span><span class="sxs-lookup"><span data-stu-id="a35f7-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35f7-104">语法</span><span class="sxs-lookup"><span data-stu-id="a35f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35f7-105">参数</span><span class="sxs-lookup"><span data-stu-id="a35f7-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="a35f7-106">[in]值为[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)枚举，用于指定是否要获取的准确或近似大小。</span><span class="sxs-lookup"><span data-stu-id="a35f7-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="a35f7-107">只有三个值都有效： cssAccurate，cssQuick，和 cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="a35f7-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="a35f7-108">cssAccurate 返回确切的存储大小，但花费的时间来计算。</span><span class="sxs-lookup"><span data-stu-id="a35f7-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="a35f7-109">cssQuick 返回大小，为安全起见，填充，但需要更少的时间来计算。</span><span class="sxs-lookup"><span data-stu-id="a35f7-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="a35f7-110">cssDiscardTransientCAs 告知`GetSaveSize`，它可以丢弃可放弃的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="a35f7-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="a35f7-111">[out]一个指向保存该文件所需的大小。</span><span class="sxs-lookup"><span data-stu-id="a35f7-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a35f7-112">备注</span><span class="sxs-lookup"><span data-stu-id="a35f7-112">Remarks</span></span>  
 <span data-ttu-id="a35f7-113">`GetSaveSize` 计算所需的空间，以字节为单位，以将该程序集和其元数据保存在当前作用域。</span><span class="sxs-lookup"><span data-stu-id="a35f7-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="a35f7-114">(调用[imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)方法将发出此数目的字节数。)</span><span class="sxs-lookup"><span data-stu-id="a35f7-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="a35f7-115">如果调用方实现[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)接口 (通过[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))，`GetSaveSize`将执行两个阶段通过优化并将其压缩的元数据。</span><span class="sxs-lookup"><span data-stu-id="a35f7-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="a35f7-116">否则，不执行任何优化。</span><span class="sxs-lookup"><span data-stu-id="a35f7-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="a35f7-117">如果执行优化，则第一步只需进行排序来优化性能的导入时搜索的元数据结构。</span><span class="sxs-lookup"><span data-stu-id="a35f7-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="a35f7-118">此步骤通常会记录移动，并且其副作用，保留供将来参考工具的令牌都无效。</span><span class="sxs-lookup"><span data-stu-id="a35f7-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="a35f7-119">元数据不会通知调用方之前这些令牌更改后的第二个过程，但是。</span><span class="sxs-lookup"><span data-stu-id="a35f7-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="a35f7-120">在第二个阶段中，各种优化的执行，旨在减少的元数据，例如优化去除 （早期绑定） 的总体大小`mdTypeRef`和`mdMemberRef`令牌的类型或成员声明中的引用时当前元数据范围。</span><span class="sxs-lookup"><span data-stu-id="a35f7-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="a35f7-121">在此阶段中，会发生另一轮标记映射。</span><span class="sxs-lookup"><span data-stu-id="a35f7-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="a35f7-122">之后此阶段中，元数据引擎通知调用方，通过其`IMapToken`接口的任何更改令牌值。</span><span class="sxs-lookup"><span data-stu-id="a35f7-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35f7-123">要求</span><span class="sxs-lookup"><span data-stu-id="a35f7-123">Requirements</span></span>  
 <span data-ttu-id="a35f7-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a35f7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35f7-125">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a35f7-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a35f7-126">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="a35f7-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a35f7-127">**.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35f7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35f7-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="a35f7-128">See also</span></span>

- [<span data-ttu-id="a35f7-129">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="a35f7-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a35f7-130">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="a35f7-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
