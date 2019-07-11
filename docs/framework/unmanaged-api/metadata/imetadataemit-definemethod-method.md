---
title: IMetaDataEmit::DefineMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4297b21970fbca4b5aa53c31680394cab358d255
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777601"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="b1001-102">IMetaDataEmit::DefineMethod 方法</span><span class="sxs-lookup"><span data-stu-id="b1001-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="b1001-103">使用指定的签名中，创建方法或全局函数的定义，并将令牌返回到该方法定义。</span><span class="sxs-lookup"><span data-stu-id="b1001-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1001-104">语法</span><span class="sxs-lookup"><span data-stu-id="b1001-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1001-105">参数</span><span class="sxs-lookup"><span data-stu-id="b1001-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b1001-106">[in]`mdTypedef`父类或父接口的方法的令牌。</span><span class="sxs-lookup"><span data-stu-id="b1001-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="b1001-107">设置`td`到`mdTokenNil`，如果您要定义全局函数。</span><span class="sxs-lookup"><span data-stu-id="b1001-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1001-108">[in]Unicode 中的成员名称。</span><span class="sxs-lookup"><span data-stu-id="b1001-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="b1001-109">[in]值为[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚举，用于指定方法或全局函数的属性。</span><span class="sxs-lookup"><span data-stu-id="b1001-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b1001-110">[in]方法签名中。</span><span class="sxs-lookup"><span data-stu-id="b1001-110">[in] The method signature.</span></span> <span data-ttu-id="b1001-111">保存签名中提供。</span><span class="sxs-lookup"><span data-stu-id="b1001-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="b1001-112">如果您需要指定任何参数的其他信息，请使用[imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b1001-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b1001-113">[in]中的字节计数`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="b1001-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="b1001-114">[in]代码的地址。</span><span class="sxs-lookup"><span data-stu-id="b1001-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b1001-115">[in]值为[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚举，用于指定该方法的实现功能。</span><span class="sxs-lookup"><span data-stu-id="b1001-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="b1001-116">[out]成员标记中。</span><span class="sxs-lookup"><span data-stu-id="b1001-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1001-117">备注</span><span class="sxs-lookup"><span data-stu-id="b1001-117">Remarks</span></span>  
 <span data-ttu-id="b1001-118">元数据 API 可保证按给定的封闭类或接口中指定的调用方发出这些方法的相同顺序保留`td`参数。</span><span class="sxs-lookup"><span data-stu-id="b1001-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="b1001-119">有关使用的其他信息`DefineMethod`和特定参数设置如下。</span><span class="sxs-lookup"><span data-stu-id="b1001-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="b1001-120">V-表中的槽</span><span class="sxs-lookup"><span data-stu-id="b1001-120">Slots in the V-table</span></span>  
 <span data-ttu-id="b1001-121">运行时使用的方法定义以设置 v 表槽。</span><span class="sxs-lookup"><span data-stu-id="b1001-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="b1001-122">在一个或多个槽需要是已跳过、 此类情况下并保持与 COM 接口布局相同的虚拟方法定义为采用槽或 v-表; 中的槽设置`dwMethodFlags`到`mdRTSpecialName`的值[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚举和名称指定为：</span><span class="sxs-lookup"><span data-stu-id="b1001-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="b1001-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="b1001-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="b1001-124">其中*SequenceNumber*是方法的序列号和*槽数*是要跳过 v 表中的槽数。</span><span class="sxs-lookup"><span data-stu-id="b1001-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="b1001-125">如果*槽数*是省略，则假定为 1。</span><span class="sxs-lookup"><span data-stu-id="b1001-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="b1001-126">这些虚拟方法不能从托管或非托管代码调用，任何尝试从托管或非托管代码中调用它们，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="b1001-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="b1001-127">其唯一用途是占用空间为 COM 集成运行时生成的 v 表中。</span><span class="sxs-lookup"><span data-stu-id="b1001-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="b1001-128">重复的方法</span><span class="sxs-lookup"><span data-stu-id="b1001-128">Duplicate Methods</span></span>  
 <span data-ttu-id="b1001-129">不应定义重复的方法。</span><span class="sxs-lookup"><span data-stu-id="b1001-129">You should not define duplicate methods.</span></span> <span data-ttu-id="b1001-130">也就是说，不应调用`DefineMethod`中的值重复一`td`， `wzName`，和`pvSig`参数。</span><span class="sxs-lookup"><span data-stu-id="b1001-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="b1001-131">(这三个参数组合在一起唯一地定义的方法。)。</span><span class="sxs-lookup"><span data-stu-id="b1001-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="b1001-132">但是，可以使用重复三次，前提是，对于其中一个方法定义，您将设置`mdPrivateScope`位`dwMethodFlags`参数。</span><span class="sxs-lookup"><span data-stu-id="b1001-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="b1001-133">(`mdPrivateScope`位意味着编译器将发出对此方法定义的引用。)</span><span class="sxs-lookup"><span data-stu-id="b1001-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="b1001-134">方法的实施信息</span><span class="sxs-lookup"><span data-stu-id="b1001-134">Method Implementation Information</span></span>  
 <span data-ttu-id="b1001-135">声明的方法时通常不知道有关方法实现的信息。</span><span class="sxs-lookup"><span data-stu-id="b1001-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="b1001-136">因此，不需要传递中的值`ulCodeRVA`并`dwImplFlags`参数调用时`DefineMethod`。</span><span class="sxs-lookup"><span data-stu-id="b1001-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="b1001-137">可以通过更高版本提供的值[imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)根据。</span><span class="sxs-lookup"><span data-stu-id="b1001-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="b1001-138">在某些情况下，如平台调用 (PInvoke) 或 COM 互操作方案中，未将提供方法正文，和`ulCodeRVA`应设置为零。</span><span class="sxs-lookup"><span data-stu-id="b1001-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="b1001-139">在这些情况下，该方法不应将标记为抽象，因为运行时将查找其实现。</span><span class="sxs-lookup"><span data-stu-id="b1001-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="b1001-140">定义一个方法的 PInvoke</span><span class="sxs-lookup"><span data-stu-id="b1001-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="b1001-141">若要通过 PInvoke 调用每个非托管函数，必须定义表示目标的非托管函数的托管的方法。</span><span class="sxs-lookup"><span data-stu-id="b1001-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="b1001-142">若要定义的托管的方法，请使用`DefineMethod`某些设置为特定值，具体取决于 PInvoke 的使用方式的参数：</span><span class="sxs-lookup"><span data-stu-id="b1001-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="b1001-143">True PInvoke-涉及到驻留在非托管 DLL 的外部的非托管方法的调用。</span><span class="sxs-lookup"><span data-stu-id="b1001-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="b1001-144">本地 PInvoke-涉及到在当前托管模块中嵌入本机非托管方法的调用。</span><span class="sxs-lookup"><span data-stu-id="b1001-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="b1001-145">下表中提供的参数设置。</span><span class="sxs-lookup"><span data-stu-id="b1001-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="b1001-146">参数</span><span class="sxs-lookup"><span data-stu-id="b1001-146">Parameter</span></span>|<span data-ttu-id="b1001-147">值为 true 的 PInvoke 的</span><span class="sxs-lookup"><span data-stu-id="b1001-147">Values for true PInvoke</span></span>|<span data-ttu-id="b1001-148">值为本地 PInvoke 的</span><span class="sxs-lookup"><span data-stu-id="b1001-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="b1001-149">设置`mdStatic`; 清除`mdSynchronized`和`mdAbstract`。</span><span class="sxs-lookup"><span data-stu-id="b1001-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="b1001-150">一个有效的公共语言运行时 (CLR) 方法签名，使用有效的参数将托管类型。</span><span class="sxs-lookup"><span data-stu-id="b1001-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="b1001-151">使用有效的参数有效的 CLR 方法签名的托管类型。</span><span class="sxs-lookup"><span data-stu-id="b1001-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="b1001-152">0</span><span class="sxs-lookup"><span data-stu-id="b1001-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="b1001-153">设置`miCil`和`miManaged`。</span><span class="sxs-lookup"><span data-stu-id="b1001-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="b1001-154">设置`miNative`和`miUnmanaged`。</span><span class="sxs-lookup"><span data-stu-id="b1001-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1001-155">要求</span><span class="sxs-lookup"><span data-stu-id="b1001-155">Requirements</span></span>  
 <span data-ttu-id="b1001-156">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1001-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1001-157">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1001-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1001-158">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="b1001-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1001-159">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1001-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1001-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1001-160">See also</span></span>

- [<span data-ttu-id="b1001-161">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="b1001-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b1001-162">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="b1001-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
