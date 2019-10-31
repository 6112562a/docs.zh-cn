---
title: Endenumeration 函数（非托管 API 参考）
description: Endenumeration 函数将枚举数重置到枚举的开头
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9e467234a45ae702a5b77a5f0fa8b75d4ff03c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124133"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="b9a68-103">BeginEnumeration 函数</span><span class="sxs-lookup"><span data-stu-id="b9a68-103">BeginEnumeration function</span></span>
<span data-ttu-id="b9a68-104">将枚举数重置回枚举的开头。</span><span class="sxs-lookup"><span data-stu-id="b9a68-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b9a68-105">语法</span><span class="sxs-lookup"><span data-stu-id="b9a68-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="b9a68-106">参数</span><span class="sxs-lookup"><span data-stu-id="b9a68-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="b9a68-107">中此参数未使用。</span><span class="sxs-lookup"><span data-stu-id="b9a68-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="b9a68-108">中指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例的指针。</span><span class="sxs-lookup"><span data-stu-id="b9a68-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="b9a68-109">中"[备注](#remarks)" 部分中描述的标志或值的按位组合，该组合控制枚举中包含的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9a68-110">返回值</span><span class="sxs-lookup"><span data-stu-id="b9a68-110">Return value</span></span>

<span data-ttu-id="b9a68-111">此函数返回的以下值是在*WbemCli*头文件中定义的，也可以在代码中将它们定义为常量：</span><span class="sxs-lookup"><span data-stu-id="b9a68-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b9a68-112">返回的常量</span><span class="sxs-lookup"><span data-stu-id="b9a68-112">Constant</span></span>  |<span data-ttu-id="b9a68-113">“值”</span><span class="sxs-lookup"><span data-stu-id="b9a68-113">Value</span></span>  |<span data-ttu-id="b9a68-114">描述</span><span class="sxs-lookup"><span data-stu-id="b9a68-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b9a68-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b9a68-115">0x80041008</span></span> | <span data-ttu-id="b9a68-116">`lEnumFlags` 中的标志组合无效，或者指定的参数无效。</span><span class="sxs-lookup"><span data-stu-id="b9a68-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="b9a68-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="b9a68-117">0x8004101d</span></span> | <span data-ttu-id="b9a68-118">对 `BeginEnumeration` 进行了第二次调用，无需对[`EndEnumeration`](endenumeration.md)进行干预。</span><span class="sxs-lookup"><span data-stu-id="b9a68-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b9a68-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b9a68-119">0x80041006</span></span> | <span data-ttu-id="b9a68-120">没有足够的内存可用于开始新的枚举。</span><span class="sxs-lookup"><span data-stu-id="b9a68-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b9a68-121">0</span><span class="sxs-lookup"><span data-stu-id="b9a68-121">0</span></span> | <span data-ttu-id="b9a68-122">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="b9a68-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b9a68-123">备注</span><span class="sxs-lookup"><span data-stu-id="b9a68-123">Remarks</span></span>

<span data-ttu-id="b9a68-124">此函数包装对[IWbemClassObject：： endenumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法的调用。</span><span class="sxs-lookup"><span data-stu-id="b9a68-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="b9a68-125">可以作为 `lEnumFlags` 参数传递的标志在*WbemCli*头文件中定义，也可以在代码中将它们定义为常量。</span><span class="sxs-lookup"><span data-stu-id="b9a68-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="b9a68-126">可以将每个组中的一个标志与任何其他组中的任何标志组合在一起。</span><span class="sxs-lookup"><span data-stu-id="b9a68-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="b9a68-127">但是，同一组中的标志互相排斥。</span><span class="sxs-lookup"><span data-stu-id="b9a68-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="b9a68-128">**组1**</span><span class="sxs-lookup"><span data-stu-id="b9a68-128">**Group 1**</span></span>

|<span data-ttu-id="b9a68-129">返回的常量</span><span class="sxs-lookup"><span data-stu-id="b9a68-129">Constant</span></span>  |<span data-ttu-id="b9a68-130">“值”</span><span class="sxs-lookup"><span data-stu-id="b9a68-130">Value</span></span>  |<span data-ttu-id="b9a68-131">描述</span><span class="sxs-lookup"><span data-stu-id="b9a68-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="b9a68-132">0x4</span><span class="sxs-lookup"><span data-stu-id="b9a68-132">0x4</span></span> | <span data-ttu-id="b9a68-133">包括仅构成密钥的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="b9a68-134">0x8</span><span class="sxs-lookup"><span data-stu-id="b9a68-134">0x8</span></span> | <span data-ttu-id="b9a68-135">包括仅为对象引用的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="b9a68-136">**组2**</span><span class="sxs-lookup"><span data-stu-id="b9a68-136">**Group 2**</span></span>

<span data-ttu-id="b9a68-137">返回的常量</span><span class="sxs-lookup"><span data-stu-id="b9a68-137">Constant</span></span>  |<span data-ttu-id="b9a68-138">“值”</span><span class="sxs-lookup"><span data-stu-id="b9a68-138">Value</span></span>  |<span data-ttu-id="b9a68-139">描述</span><span class="sxs-lookup"><span data-stu-id="b9a68-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="b9a68-140">0x30</span><span class="sxs-lookup"><span data-stu-id="b9a68-140">0x30</span></span> | <span data-ttu-id="b9a68-141">仅限枚举到系统属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="b9a68-142">0x40</span><span class="sxs-lookup"><span data-stu-id="b9a68-142">0x40</span></span> | <span data-ttu-id="b9a68-143">包括本地和传播属性，但不包括枚举中的系统属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="b9a68-144">对于类：</span><span class="sxs-lookup"><span data-stu-id="b9a68-144">For classes:</span></span>

<span data-ttu-id="b9a68-145">返回的常量</span><span class="sxs-lookup"><span data-stu-id="b9a68-145">Constant</span></span>  |<span data-ttu-id="b9a68-146">“值”</span><span class="sxs-lookup"><span data-stu-id="b9a68-146">Value</span></span>  |<span data-ttu-id="b9a68-147">描述</span><span class="sxs-lookup"><span data-stu-id="b9a68-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="b9a68-148">0x100</span><span class="sxs-lookup"><span data-stu-id="b9a68-148">0x100</span></span> | <span data-ttu-id="b9a68-149">将枚举限制为在类定义中重写的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="b9a68-150">0x100</span><span class="sxs-lookup"><span data-stu-id="b9a68-150">0x100</span></span> | <span data-ttu-id="b9a68-151">将枚举限制为在当前类定义中重写的属性和在类中定义的新属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="b9a68-152">0x300</span><span class="sxs-lookup"><span data-stu-id="b9a68-152">0x300</span></span> | <span data-ttu-id="b9a68-153">要应用于 `lEnumFlags` 值以检查是否设置了 `WBEM_FLAG_CLASS_OVERRIDES_ONLY` 或 `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` 的掩码（而不是标志）。</span><span class="sxs-lookup"><span data-stu-id="b9a68-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="b9a68-154">0x10</span><span class="sxs-lookup"><span data-stu-id="b9a68-154">0x10</span></span> | <span data-ttu-id="b9a68-155">将枚举限制为在类本身中定义或修改的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="b9a68-156">0x20</span><span class="sxs-lookup"><span data-stu-id="b9a68-156">0x20</span></span> | <span data-ttu-id="b9a68-157">将枚举限制为从基类继承的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="b9a68-158">对于实例：</span><span class="sxs-lookup"><span data-stu-id="b9a68-158">For instances:</span></span>

<span data-ttu-id="b9a68-159">返回的常量</span><span class="sxs-lookup"><span data-stu-id="b9a68-159">Constant</span></span>  |<span data-ttu-id="b9a68-160">“值”</span><span class="sxs-lookup"><span data-stu-id="b9a68-160">Value</span></span>  |<span data-ttu-id="b9a68-161">描述</span><span class="sxs-lookup"><span data-stu-id="b9a68-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="b9a68-162">0x10</span><span class="sxs-lookup"><span data-stu-id="b9a68-162">0x10</span></span> | <span data-ttu-id="b9a68-163">将枚举限制为在类本身中定义或修改的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="b9a68-164">0x20</span><span class="sxs-lookup"><span data-stu-id="b9a68-164">0x20</span></span> | <span data-ttu-id="b9a68-165">将枚举限制为从基类继承的属性。</span><span class="sxs-lookup"><span data-stu-id="b9a68-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="b9a68-166">要求</span><span class="sxs-lookup"><span data-stu-id="b9a68-166">Requirements</span></span>  
 <span data-ttu-id="b9a68-167">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9a68-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a68-168">**标头：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="b9a68-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b9a68-169">**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a68-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a68-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9a68-170">See also</span></span>

- [<span data-ttu-id="b9a68-171">WMI 和性能计数器（非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="b9a68-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
