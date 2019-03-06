---
title: GetPropertyOrigin 函数 （非托管 API 参考）
description: GetPropertyOrigin 函数将确定所声明的属性的类。
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42e5cd6ee438b33fd07fd7c3242cc3c2a6513dd9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368868"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="584c0-103">GetPropertyOrigin 函数</span><span class="sxs-lookup"><span data-stu-id="584c0-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="584c0-104">确定声明方法的类。</span><span class="sxs-lookup"><span data-stu-id="584c0-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="584c0-105">语法</span><span class="sxs-lookup"><span data-stu-id="584c0-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="584c0-106">参数</span><span class="sxs-lookup"><span data-stu-id="584c0-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="584c0-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="584c0-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="584c0-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="584c0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="584c0-109">[in]正在请求其所属的类的对象属性的名称。</span><span class="sxs-lookup"><span data-stu-id="584c0-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="584c0-110">[out]接收拥有属性的类的名称。</span><span class="sxs-lookup"><span data-stu-id="584c0-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="584c0-111">返回值</span><span class="sxs-lookup"><span data-stu-id="584c0-111">Return value</span></span>

<span data-ttu-id="584c0-112">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="584c0-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="584c0-113">返回的常量</span><span class="sxs-lookup"><span data-stu-id="584c0-113">Constant</span></span>  |<span data-ttu-id="584c0-114">“值”</span><span class="sxs-lookup"><span data-stu-id="584c0-114">Value</span></span>  |<span data-ttu-id="584c0-115">描述</span><span class="sxs-lookup"><span data-stu-id="584c0-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="584c0-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="584c0-116">0x80041001</span></span> | <span data-ttu-id="584c0-117">已存在时的常见错误。</span><span class="sxs-lookup"><span data-stu-id="584c0-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="584c0-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="584c0-118">0x80041002</span></span> | <span data-ttu-id="584c0-119">找不到指定的属性。</span><span class="sxs-lookup"><span data-stu-id="584c0-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="584c0-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="584c0-120">0x80041008</span></span> | <span data-ttu-id="584c0-121">参数不是有效的。</span><span class="sxs-lookup"><span data-stu-id="584c0-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="584c0-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="584c0-122">0x80041006</span></span> | <span data-ttu-id="584c0-123">没有足够的内存是可用于完成该操作。</span><span class="sxs-lookup"><span data-stu-id="584c0-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="584c0-124">0</span><span class="sxs-lookup"><span data-stu-id="584c0-124">0</span></span> | <span data-ttu-id="584c0-125">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="584c0-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="584c0-126">备注</span><span class="sxs-lookup"><span data-stu-id="584c0-126">Remarks</span></span>

<span data-ttu-id="584c0-127">此函数包装对的调用[IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin)方法。</span><span class="sxs-lookup"><span data-stu-id="584c0-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="584c0-128">类可以从一个或多个基类继承属性，因为开发人员经常需要确定在其中定义给定的方法的属性。</span><span class="sxs-lookup"><span data-stu-id="584c0-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="584c0-129">`pstrClassName`参数必须指向有效`BSTR`由于这是调用该函数之前`out`参数; 此函数返回后，会释放指针。</span><span class="sxs-lookup"><span data-stu-id="584c0-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="584c0-130">要求</span><span class="sxs-lookup"><span data-stu-id="584c0-130">Requirements</span></span>

<span data-ttu-id="584c0-131">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="584c0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="584c0-132">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="584c0-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="584c0-133">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="584c0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="584c0-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="584c0-134">See also</span></span>

- [<span data-ttu-id="584c0-135">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="584c0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)