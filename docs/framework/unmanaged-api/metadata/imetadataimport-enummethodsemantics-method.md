---
title: IMetaDataImport::EnumMethodSemantics 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16cfa6df6251cd67860155cb8092e77a835eaaef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992415"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="4ed95-102">IMetaDataImport::EnumMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="4ed95-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="4ed95-103">枚举与指定方法相关的属性和属性更改事件。</span><span class="sxs-lookup"><span data-stu-id="4ed95-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed95-104">语法</span><span class="sxs-lookup"><span data-stu-id="4ed95-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ed95-105">参数</span><span class="sxs-lookup"><span data-stu-id="4ed95-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4ed95-106">[in、 out]一个指向枚举器。</span><span class="sxs-lookup"><span data-stu-id="4ed95-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4ed95-107">对于首次调用此方法，这必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="4ed95-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="4ed95-108">[in]枚举的作用域限制的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="4ed95-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="4ed95-109">[out]用于存储事件或属性的数组。</span><span class="sxs-lookup"><span data-stu-id="4ed95-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4ed95-110">[in] `rEventProp` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="4ed95-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="4ed95-111">[out]事件或属性中返回的数`rEventProp`。</span><span class="sxs-lookup"><span data-stu-id="4ed95-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ed95-112">返回值</span><span class="sxs-lookup"><span data-stu-id="4ed95-112">Return Value</span></span>  
  
|<span data-ttu-id="4ed95-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ed95-113">HRESULT</span></span>|<span data-ttu-id="4ed95-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ed95-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4ed95-115">`EnumMethodSemantics` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="4ed95-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4ed95-116">没有任何事件或属性，以枚举。</span><span class="sxs-lookup"><span data-stu-id="4ed95-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="4ed95-117">在这种情况下，`pcEventProp`为零。</span><span class="sxs-lookup"><span data-stu-id="4ed95-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ed95-118">备注</span><span class="sxs-lookup"><span data-stu-id="4ed95-118">Remarks</span></span>  
 <span data-ttu-id="4ed95-119">许多公共语言运行时类型定义*属性*`Changed`事件并`On`*属性*`Changed`方法与它们的属性。</span><span class="sxs-lookup"><span data-stu-id="4ed95-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="4ed95-120">例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>类型定义<xref:System.Windows.Forms.Control.Font%2A>属性，<xref:System.Windows.Forms.Control.FontChanged>事件，和一个<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4ed95-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="4ed95-121">Set 访问器方法的<xref:System.Windows.Forms.Control.Font%2A>属性调用<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法，从而引发<xref:System.Windows.Forms.Control.FontChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="4ed95-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="4ed95-122">将调用`EnumMethodSemantics`使用的 MethodDef<xref:System.Windows.Forms.Control.OnFontChanged%2A>来获得对引用<xref:System.Windows.Forms.Control.Font%2A>属性和<xref:System.Windows.Forms.Control.FontChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="4ed95-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ed95-123">要求</span><span class="sxs-lookup"><span data-stu-id="4ed95-123">Requirements</span></span>  
 <span data-ttu-id="4ed95-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ed95-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed95-125">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ed95-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ed95-126">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="4ed95-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ed95-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed95-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed95-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ed95-128">See also</span></span>

- [<span data-ttu-id="4ed95-129">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="4ed95-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4ed95-130">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="4ed95-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
