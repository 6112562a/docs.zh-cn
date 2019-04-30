---
title: GetPropertyQualifierSet 函数 （非托管 API 参考）
description: GetPropertyQualifierSet 函数检索设置为属性的限定符。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdb9f748279e4e74c0dbd1ced1f48e3a24b9904d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959531"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="e5634-103">GetPropertyQualifierSet 函数</span><span class="sxs-lookup"><span data-stu-id="e5634-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="e5634-104">检索特定属性的限定符集。</span><span class="sxs-lookup"><span data-stu-id="e5634-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e5634-105">语法</span><span class="sxs-lookup"><span data-stu-id="e5634-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="e5634-106">参数</span><span class="sxs-lookup"><span data-stu-id="e5634-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e5634-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="e5634-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e5634-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="e5634-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="e5634-109">[in]属性名称。</span><span class="sxs-lookup"><span data-stu-id="e5634-109">[in] The property  name.</span></span> <span data-ttu-id="e5634-110">`wszProperty` 必须指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="e5634-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="e5634-111">[out]接收允许访问的属性限定符的接口指针。</span><span class="sxs-lookup"><span data-stu-id="e5634-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="e5634-112">`ppQualSet` 不能为 `null`。</span><span class="sxs-lookup"><span data-stu-id="e5634-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="e5634-113">如果发生错误，未返回一个新的对象，并将指针设置为指向`null`。</span><span class="sxs-lookup"><span data-stu-id="e5634-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5634-114">返回值</span><span class="sxs-lookup"><span data-stu-id="e5634-114">Return value</span></span>

<span data-ttu-id="e5634-115">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="e5634-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5634-116">返回的常量</span><span class="sxs-lookup"><span data-stu-id="e5634-116">Constant</span></span>  |<span data-ttu-id="e5634-117">“值”</span><span class="sxs-lookup"><span data-stu-id="e5634-117">Value</span></span>  |<span data-ttu-id="e5634-118">描述</span><span class="sxs-lookup"><span data-stu-id="e5634-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e5634-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e5634-119">0x80041001</span></span> | <span data-ttu-id="e5634-120">已存在时的常见错误。</span><span class="sxs-lookup"><span data-stu-id="e5634-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="e5634-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e5634-121">0x80041002</span></span> | <span data-ttu-id="e5634-122">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="e5634-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e5634-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e5634-123">0x80041006</span></span> | <span data-ttu-id="e5634-124">没有足够的内存是可用于完成该操作。</span><span class="sxs-lookup"><span data-stu-id="e5634-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5634-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5634-125">0x80041008</span></span> | <span data-ttu-id="e5634-126">参数是`null`。</span><span class="sxs-lookup"><span data-stu-id="e5634-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="e5634-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="e5634-127">0x80041030</span></span> | <span data-ttu-id="e5634-128">该函数尝试获取系统属性的限定符。</span><span class="sxs-lookup"><span data-stu-id="e5634-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5634-129">0</span><span class="sxs-lookup"><span data-stu-id="e5634-129">0</span></span> | <span data-ttu-id="e5634-130">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="e5634-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e5634-131">备注</span><span class="sxs-lookup"><span data-stu-id="e5634-131">Remarks</span></span>

<span data-ttu-id="e5634-132">此函数包装对的调用[IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)方法。</span><span class="sxs-lookup"><span data-stu-id="e5634-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="e5634-133">当前对象是 CIM 类定义时，才支持对此函数的调用。</span><span class="sxs-lookup"><span data-stu-id="e5634-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="e5634-134">方法操作不适用于[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向 CIM 实例的指针。</span><span class="sxs-lookup"><span data-stu-id="e5634-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="e5634-135">因为每个方法可能具有其自己的限定符[IWbemQualifierSet 指针](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)允许调用方添加、 编辑或删除这些限定符。</span><span class="sxs-lookup"><span data-stu-id="e5634-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="e5634-136">系统属性包含没有限定符，因为该函数将返回`WBEM_E_SYSTEM_PROPERTY`如果你尝试获取[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)系统属性的指针。</span><span class="sxs-lookup"><span data-stu-id="e5634-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5634-137">要求</span><span class="sxs-lookup"><span data-stu-id="e5634-137">Requirements</span></span>

<span data-ttu-id="e5634-138">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5634-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e5634-139">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5634-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e5634-140">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5634-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e5634-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5634-141">See also</span></span>

- [<span data-ttu-id="e5634-142">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="e5634-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)