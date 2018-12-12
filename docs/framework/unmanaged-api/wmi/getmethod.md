---
title: GetMethod 函数 （非托管 API 参考）
description: GetMethod 函数检索有关方法的信息。
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 133e056663b208f2a0d12f05f31daaca95676dc5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152313"
---
# <a name="getmethod-function"></a><span data-ttu-id="4e24e-103">GetMethod 函数</span><span class="sxs-lookup"><span data-stu-id="4e24e-103">GetMethod function</span></span>
<span data-ttu-id="4e24e-104">检索有关指定方法的信息。</span><span class="sxs-lookup"><span data-stu-id="4e24e-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4e24e-105">语法</span><span class="sxs-lookup"><span data-stu-id="4e24e-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="4e24e-106">参数</span><span class="sxs-lookup"><span data-stu-id="4e24e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4e24e-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="4e24e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4e24e-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="4e24e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="4e24e-109">[in]方法名称。</span><span class="sxs-lookup"><span data-stu-id="4e24e-109">[in] The method name.</span></span> <span data-ttu-id="4e24e-110">此参数不能`null`必须指向有效和`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="4e24e-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="4e24e-111">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="4e24e-111">[in] Reserved.</span></span> <span data-ttu-id="4e24e-112">此参数必须为 0。</span><span class="sxs-lookup"><span data-stu-id="4e24e-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="4e24e-113">[out]指向的地址的指针[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)介绍的方法在 paramteers 的实例。</span><span class="sxs-lookup"><span data-stu-id="4e24e-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="4e24e-114">如果设置为，则忽略此参数`null`。</span><span class="sxs-lookup"><span data-stu-id="4e24e-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="4e24e-115">[out]指向的地址的指针[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例，它描述的方法的 out 参数。</span><span class="sxs-lookup"><span data-stu-id="4e24e-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="4e24e-116">如果设置为，则忽略此参数`null`。</span><span class="sxs-lookup"><span data-stu-id="4e24e-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4e24e-117">返回值</span><span class="sxs-lookup"><span data-stu-id="4e24e-117">Return value</span></span>

<span data-ttu-id="4e24e-118">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="4e24e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4e24e-119">返回的常量</span><span class="sxs-lookup"><span data-stu-id="4e24e-119">Constant</span></span>  |<span data-ttu-id="4e24e-120">值</span><span class="sxs-lookup"><span data-stu-id="4e24e-120">Value</span></span>  |<span data-ttu-id="4e24e-121">描述</span><span class="sxs-lookup"><span data-stu-id="4e24e-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4e24e-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4e24e-122">0x80041002</span></span> | <span data-ttu-id="4e24e-123">找不到指定的属性。</span><span class="sxs-lookup"><span data-stu-id="4e24e-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4e24e-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4e24e-124">0x80041006</span></span> | <span data-ttu-id="4e24e-125">没有足够的内存是可用于完成该操作。</span><span class="sxs-lookup"><span data-stu-id="4e24e-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4e24e-126">0</span><span class="sxs-lookup"><span data-stu-id="4e24e-126">0</span></span> | <span data-ttu-id="4e24e-127">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="4e24e-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4e24e-128">备注</span><span class="sxs-lookup"><span data-stu-id="4e24e-128">Remarks</span></span>

<span data-ttu-id="4e24e-129">此函数包装对的调用[IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。</span><span class="sxs-lookup"><span data-stu-id="4e24e-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="4e24e-130">Windows 管理可以设置[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向`null`如果方法没有在参数。</span><span class="sxs-lookup"><span data-stu-id="4e24e-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="4e24e-131">在中`ppInSignature`并`ppOutSignature`描述 in 和 out 参数，分别为中的属性`IWbemClassObject`系统类的实例[_Parameters](/windows/desktop/WmiSdk/--parameters)。</span><span class="sxs-lookup"><span data-stu-id="4e24e-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="4e24e-132">中的属性`ppInsignature`名为`Param` *n*，其中*n*是方法签名中参数的位置 (如`Param1`， `Param2`，等等。)。</span><span class="sxs-lookup"><span data-stu-id="4e24e-132">The properties in `ppInsignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="4e24e-133">中的属性`ppOutSignature`也称为`Param` *n*，并返回值名为`ReturnValue`。</span><span class="sxs-lookup"><span data-stu-id="4e24e-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="4e24e-134">有关详细信息和示例，请参阅[IWbemClassObject::GetMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)。</span><span class="sxs-lookup"><span data-stu-id="4e24e-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="4e24e-135">要求</span><span class="sxs-lookup"><span data-stu-id="4e24e-135">Requirements</span></span>  
<span data-ttu-id="4e24e-136">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e24e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e24e-137">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4e24e-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4e24e-138">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4e24e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e24e-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e24e-139">See also</span></span>  
[<span data-ttu-id="4e24e-140">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="4e24e-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
