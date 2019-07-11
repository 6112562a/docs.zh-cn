---
title: Get 函数 （非托管 API 参考）
description: Get 函数检索指定的属性值。
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1f838c26d45c0f3cfbd50ac0ce02d234b82ddae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746656"
---
# <a name="get-function"></a><span data-ttu-id="a23ca-103">Get 函数</span><span class="sxs-lookup"><span data-stu-id="a23ca-103">Get function</span></span>

<span data-ttu-id="a23ca-104">检索指定的属性值，如果它存在。</span><span class="sxs-lookup"><span data-stu-id="a23ca-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a23ca-105">语法</span><span class="sxs-lookup"><span data-stu-id="a23ca-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a><span data-ttu-id="a23ca-106">参数</span><span class="sxs-lookup"><span data-stu-id="a23ca-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a23ca-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="a23ca-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a23ca-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="a23ca-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="a23ca-109">[in]属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a23ca-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="a23ca-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="a23ca-110">[in] Reserved.</span></span> <span data-ttu-id="a23ca-111">此参数必须为 0。</span><span class="sxs-lookup"><span data-stu-id="a23ca-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="a23ca-112">[out]如果该函数将返回成功，包含值的`wszName`属性。</span><span class="sxs-lookup"><span data-stu-id="a23ca-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="a23ca-113">`pval`参数分配正确的类型和限定符值。</span><span class="sxs-lookup"><span data-stu-id="a23ca-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="a23ca-114">[out]如果该函数将返回成功，包含[CIM 类型的常量](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration)，该值指示属性类型。</span><span class="sxs-lookup"><span data-stu-id="a23ca-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="a23ca-115">其值也可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="a23ca-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="a23ca-116">[out]如果该函数将返回成功，接收有关源的属性的信息。</span><span class="sxs-lookup"><span data-stu-id="a23ca-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="a23ca-117">其值可以是`null`，或定义中的以下 WBEM_FLAVOR_TYPE 常量之一*WbemCli.h*标头文件：</span><span class="sxs-lookup"><span data-stu-id="a23ca-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="a23ca-118">返回的常量</span><span class="sxs-lookup"><span data-stu-id="a23ca-118">Constant</span></span>  |<span data-ttu-id="a23ca-119">值</span><span class="sxs-lookup"><span data-stu-id="a23ca-119">Value</span></span>  |<span data-ttu-id="a23ca-120">描述</span><span class="sxs-lookup"><span data-stu-id="a23ca-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="a23ca-121">0x40</span><span class="sxs-lookup"><span data-stu-id="a23ca-121">0x40</span></span> | <span data-ttu-id="a23ca-122">该属性是标准系统属性。</span><span class="sxs-lookup"><span data-stu-id="a23ca-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="a23ca-123">0x20</span><span class="sxs-lookup"><span data-stu-id="a23ca-123">0x20</span></span> | <span data-ttu-id="a23ca-124">类：属性继承自的父类。</span><span class="sxs-lookup"><span data-stu-id="a23ca-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="a23ca-125">实例：属性，继承自的父类，而未已修改的实例。</span><span class="sxs-lookup"><span data-stu-id="a23ca-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="a23ca-126">0</span><span class="sxs-lookup"><span data-stu-id="a23ca-126">0</span></span> | <span data-ttu-id="a23ca-127">类：属性属于派生类。</span><span class="sxs-lookup"><span data-stu-id="a23ca-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="a23ca-128">实例：实例; 修改属性也就是说，却提供了值，或限定符已添加或修改。</span><span class="sxs-lookup"><span data-stu-id="a23ca-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="a23ca-129">返回值</span><span class="sxs-lookup"><span data-stu-id="a23ca-129">Return value</span></span>

<span data-ttu-id="a23ca-130">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="a23ca-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a23ca-131">返回的常量</span><span class="sxs-lookup"><span data-stu-id="a23ca-131">Constant</span></span>  |<span data-ttu-id="a23ca-132">值</span><span class="sxs-lookup"><span data-stu-id="a23ca-132">Value</span></span>  |<span data-ttu-id="a23ca-133">描述</span><span class="sxs-lookup"><span data-stu-id="a23ca-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a23ca-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a23ca-134">0x80041001</span></span> | <span data-ttu-id="a23ca-135">已存在时的常见错误。</span><span class="sxs-lookup"><span data-stu-id="a23ca-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a23ca-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a23ca-136">0x80041008</span></span> | <span data-ttu-id="a23ca-137">一个或多个参数是无效的。</span><span class="sxs-lookup"><span data-stu-id="a23ca-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a23ca-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a23ca-138">0x80041002</span></span> | <span data-ttu-id="a23ca-139">找不到指定的属性。</span><span class="sxs-lookup"><span data-stu-id="a23ca-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a23ca-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a23ca-140">0x80041006</span></span> | <span data-ttu-id="a23ca-141">没有足够的内存是可用于完成该操作。</span><span class="sxs-lookup"><span data-stu-id="a23ca-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a23ca-142">0</span><span class="sxs-lookup"><span data-stu-id="a23ca-142">0</span></span> | <span data-ttu-id="a23ca-143">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="a23ca-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a23ca-144">备注</span><span class="sxs-lookup"><span data-stu-id="a23ca-144">Remarks</span></span>

<span data-ttu-id="a23ca-145">此函数包装对的调用[IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法。</span><span class="sxs-lookup"><span data-stu-id="a23ca-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="a23ca-146">`Get`函数还可以返回系统属性。</span><span class="sxs-lookup"><span data-stu-id="a23ca-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="a23ca-147">`pVal`自变量分配正确的类型和值限定符和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函数</span><span class="sxs-lookup"><span data-stu-id="a23ca-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="a23ca-148">要求</span><span class="sxs-lookup"><span data-stu-id="a23ca-148">Requirements</span></span>

 <span data-ttu-id="a23ca-149">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a23ca-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a23ca-150">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a23ca-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="a23ca-151">**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a23ca-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a23ca-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="a23ca-152">See also</span></span>

- [<span data-ttu-id="a23ca-153">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="a23ca-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
