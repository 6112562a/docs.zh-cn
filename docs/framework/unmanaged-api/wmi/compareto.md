---
title: CompareTo 函数 （非托管 API 参考）
description: CompareTo 函数将对象与其他 WMI 对象进行比较。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3566b9b8a3b4183f936c82c39c38dc5daa3aeae1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636681"
---
# <a name="compareto-function"></a><span data-ttu-id="9819b-103">CompareTo 函数</span><span class="sxs-lookup"><span data-stu-id="9819b-103">CompareTo function</span></span>

<span data-ttu-id="9819b-104">将对象与另一个 Windows 管理对象进行比较。</span><span class="sxs-lookup"><span data-stu-id="9819b-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9819b-105">语法</span><span class="sxs-lookup"><span data-stu-id="9819b-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="9819b-106">参数</span><span class="sxs-lookup"><span data-stu-id="9819b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="9819b-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="9819b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="9819b-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="9819b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="9819b-109">[in]指定要考虑的比较的对象特征的标志的按位组合。</span><span class="sxs-lookup"><span data-stu-id="9819b-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="9819b-110">请参阅[备注](#remarks)部分，了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="9819b-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="9819b-111">[in]进行比较的对象。</span><span class="sxs-lookup"><span data-stu-id="9819b-111">[in] The object for comparison.</span></span> <span data-ttu-id="9819b-112">`pCompareTo` 必须是有效[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例; 它不能为`null`。</span><span class="sxs-lookup"><span data-stu-id="9819b-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9819b-113">返回值</span><span class="sxs-lookup"><span data-stu-id="9819b-113">Return value</span></span>

<span data-ttu-id="9819b-114">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="9819b-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9819b-115">返回的常量</span><span class="sxs-lookup"><span data-stu-id="9819b-115">Constant</span></span>  |<span data-ttu-id="9819b-116">值</span><span class="sxs-lookup"><span data-stu-id="9819b-116">Value</span></span>  |<span data-ttu-id="9819b-117">描述</span><span class="sxs-lookup"><span data-stu-id="9819b-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="9819b-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9819b-118">0x80041001</span></span> | <span data-ttu-id="9819b-119">发生未知的错误。</span><span class="sxs-lookup"><span data-stu-id="9819b-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9819b-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9819b-120">0x80041008</span></span> | <span data-ttu-id="9819b-121">参数无效。</span><span class="sxs-lookup"><span data-stu-id="9819b-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="9819b-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="9819b-122">0x8004101d</span></span> | <span data-ttu-id="9819b-123">第二次调用`BeginEnumeration`而无需对的干预调用进行[ `EndEnumeration` ](endenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="9819b-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9819b-124">0</span><span class="sxs-lookup"><span data-stu-id="9819b-124">0</span></span> | <span data-ttu-id="9819b-125">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="9819b-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="9819b-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="9819b-126">0x40003</span></span> | <span data-ttu-id="9819b-127">对象不同。</span><span class="sxs-lookup"><span data-stu-id="9819b-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="9819b-128">0</span><span class="sxs-lookup"><span data-stu-id="9819b-128">0</span></span> | <span data-ttu-id="9819b-129">对象是相同的基础的比较标志。</span><span class="sxs-lookup"><span data-stu-id="9819b-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9819b-130">备注</span><span class="sxs-lookup"><span data-stu-id="9819b-130">Remarks</span></span>

<span data-ttu-id="9819b-131">此函数包装对的调用[IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)方法。</span><span class="sxs-lookup"><span data-stu-id="9819b-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="9819b-132">可以作为传递的标志`lEnumFlags`中定义参数*WbemCli.h*标头文件，也可以在定义它们为常量在代码中。</span><span class="sxs-lookup"><span data-stu-id="9819b-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="9819b-133">通过指定以下标志的按位组合，可以指定在比较中涉及的各个特征：</span><span class="sxs-lookup"><span data-stu-id="9819b-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="9819b-134">返回的常量</span><span class="sxs-lookup"><span data-stu-id="9819b-134">Constant</span></span>  |<span data-ttu-id="9819b-135">值</span><span class="sxs-lookup"><span data-stu-id="9819b-135">Value</span></span>  |<span data-ttu-id="9819b-136">描述</span><span class="sxs-lookup"><span data-stu-id="9819b-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="9819b-137">2</span><span class="sxs-lookup"><span data-stu-id="9819b-137">2</span></span> | <span data-ttu-id="9819b-138">忽略源 （在服务器和它们原来的位置的命名空间）。</span><span class="sxs-lookup"><span data-stu-id="9819b-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="9819b-139">1</span><span class="sxs-lookup"><span data-stu-id="9819b-139">1</span></span> | <span data-ttu-id="9819b-140">忽略所有限定符 (包括**键**并**动态**)</span><span class="sxs-lookup"><span data-stu-id="9819b-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="9819b-141">4</span><span class="sxs-lookup"><span data-stu-id="9819b-141">4</span></span> | <span data-ttu-id="9819b-142">忽略属性的默认的值。</span><span class="sxs-lookup"><span data-stu-id="9819b-142">Ignore default values of properties.</span></span> <span data-ttu-id="9819b-143">此标志仅适用于的类的比较。</span><span class="sxs-lookup"><span data-stu-id="9819b-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="9819b-144">0x20</span><span class="sxs-lookup"><span data-stu-id="9819b-144">0x20</span></span> | <span data-ttu-id="9819b-145">忽略限定符特色信息。</span><span class="sxs-lookup"><span data-stu-id="9819b-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="9819b-146">此标志仍将限定符考虑在内，但会忽略风格差别，如传播规则和重写的限制。</span><span class="sxs-lookup"><span data-stu-id="9819b-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="9819b-147">0x10</span><span class="sxs-lookup"><span data-stu-id="9819b-147">0x10</span></span> | <span data-ttu-id="9819b-148">忽略大小写比较字符串值。</span><span class="sxs-lookup"><span data-stu-id="9819b-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="9819b-149">这同时适用于字符串和限定符值。</span><span class="sxs-lookup"><span data-stu-id="9819b-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="9819b-150">属性名称和限定符名称比较始终是区分大小写，而不考虑是否设置了此标志。</span><span class="sxs-lookup"><span data-stu-id="9819b-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="9819b-151">0x8</span><span class="sxs-lookup"><span data-stu-id="9819b-151">0x8</span></span> | <span data-ttu-id="9819b-152">假定要比较的对象都是相同的类的实例。</span><span class="sxs-lookup"><span data-stu-id="9819b-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="9819b-153">因此，此标志将与实例相关信息进行比较。</span><span class="sxs-lookup"><span data-stu-id="9819b-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="9819b-154">使用此标志来优化性能。</span><span class="sxs-lookup"><span data-stu-id="9819b-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="9819b-155">如果对象不属于同一个类，则结果不确定。</span><span class="sxs-lookup"><span data-stu-id="9819b-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="9819b-156">也可以指定单个复合标志，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9819b-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="9819b-157">返回的常量</span><span class="sxs-lookup"><span data-stu-id="9819b-157">Constant</span></span>  |<span data-ttu-id="9819b-158">值</span><span class="sxs-lookup"><span data-stu-id="9819b-158">Value</span></span>  |<span data-ttu-id="9819b-159">Description</span><span class="sxs-lookup"><span data-stu-id="9819b-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="9819b-160">0</span><span class="sxs-lookup"><span data-stu-id="9819b-160">0</span></span> | <span data-ttu-id="9819b-161">请考虑在比较中的所有功能。</span><span class="sxs-lookup"><span data-stu-id="9819b-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="9819b-162">要求</span><span class="sxs-lookup"><span data-stu-id="9819b-162">Requirements</span></span>

<span data-ttu-id="9819b-163">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9819b-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9819b-164">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9819b-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="9819b-165">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9819b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9819b-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="9819b-166">See also</span></span>

- [<span data-ttu-id="9819b-167">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="9819b-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
