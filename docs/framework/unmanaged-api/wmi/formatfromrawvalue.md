---
title: FormatFromRawValue 函数 （非托管 API 参考）
description: FormatFromRawValue 函数将转换为指定格式的原始性能数据。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47f92122eddf3cc8e6aec19d75fd2a95f76e9973
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746705"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="1ea1d-103">FormatFromRawValue 函数</span><span class="sxs-lookup"><span data-stu-id="1ea1d-103">FormatFromRawValue function</span></span>
<span data-ttu-id="1ea1d-104">如果格式转换是基于时间的，则将一个或两个原始性能数据值转换为指定格式。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1ea1d-105">语法</span><span class="sxs-lookup"><span data-stu-id="1ea1d-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a><span data-ttu-id="1ea1d-106">参数</span><span class="sxs-lookup"><span data-stu-id="1ea1d-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="1ea1d-107">[in]计数器类型。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-107">[in] The counter type.</span></span> <span data-ttu-id="1ea1d-108">计数器类型的列表，请参阅[WMI 性能计数器类型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="1ea1d-109">`dwCounterType` 可以是任何计数器类型除外`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="1ea1d-110">[in]若要将原始性能数据转换为的格式。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="1ea1d-111">它可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="1ea1d-111">It can be one of the following values:</span></span>

|<span data-ttu-id="1ea1d-112">返回的常量</span><span class="sxs-lookup"><span data-stu-id="1ea1d-112">Constant</span></span>  |<span data-ttu-id="1ea1d-113">值</span><span class="sxs-lookup"><span data-stu-id="1ea1d-113">Value</span></span>  |<span data-ttu-id="1ea1d-114">描述</span><span class="sxs-lookup"><span data-stu-id="1ea1d-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="1ea1d-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="1ea1d-115">0x00000200</span></span> | <span data-ttu-id="1ea1d-116">返回作为双精度浮点值的计算的值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="1ea1d-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="1ea1d-117">0x00000400</span></span> | <span data-ttu-id="1ea1d-118">以 64 位整数形式返回计算的值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="1ea1d-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="1ea1d-119">0x00000100</span></span> | <span data-ttu-id="1ea1d-120">返回作为 32 位整数的计算的值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="1ea1d-121">其中一个以前的值可以是或运算的以下缩放标志之一：</span><span class="sxs-lookup"><span data-stu-id="1ea1d-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="1ea1d-122">返回的常量</span><span class="sxs-lookup"><span data-stu-id="1ea1d-122">Constant</span></span>  |<span data-ttu-id="1ea1d-123">值</span><span class="sxs-lookup"><span data-stu-id="1ea1d-123">Value</span></span>  |<span data-ttu-id="1ea1d-124">描述</span><span class="sxs-lookup"><span data-stu-id="1ea1d-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="1ea1d-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="1ea1d-125">0x00001000</span></span> | <span data-ttu-id="1ea1d-126">不适用于计数器的比例因子。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="1ea1d-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="1ea1d-127">0x00002000</span></span> | <span data-ttu-id="1ea1d-128">最终值乘以 1,000。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="1ea1d-129">[in]时间基准，如有必要格式转换为指向的指针。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="1ea1d-130">如果没有格式转换所需时间基本信息，则忽略此参数的值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="1ea1d-131">`pRawValue1`\ [in] 一个指向[ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter)结构，它表示原始性能值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="1ea1d-132">[in]一个指向[ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter)结构，它表示第二个原始性能值。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="1ea1d-133">如果第二个原始性能值不是必需的此参数应为`null`。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="1ea1d-134">[out]一个指向[ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue)接收格式化的性能值的结构。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ea1d-135">返回值</span><span class="sxs-lookup"><span data-stu-id="1ea1d-135">Return value</span></span>

<span data-ttu-id="1ea1d-136">此函数返回以下值：</span><span class="sxs-lookup"><span data-stu-id="1ea1d-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="1ea1d-137">返回的常量</span><span class="sxs-lookup"><span data-stu-id="1ea1d-137">Constant</span></span>  |<span data-ttu-id="1ea1d-138">值</span><span class="sxs-lookup"><span data-stu-id="1ea1d-138">Value</span></span>  |<span data-ttu-id="1ea1d-139">Description</span><span class="sxs-lookup"><span data-stu-id="1ea1d-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="1ea1d-140">0</span><span class="sxs-lookup"><span data-stu-id="1ea1d-140">0</span></span> | <span data-ttu-id="1ea1d-141">函数调用是成功的。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="1ea1d-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="1ea1d-142">0xC0000BBD</span></span> | <span data-ttu-id="1ea1d-143">必需的参数已丢失或不正确。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="1ea1d-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="1ea1d-144">0xC0000BBC</span></span> | <span data-ttu-id="1ea1d-145">句柄不是有效的 PDH 对象。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1ea1d-146">备注</span><span class="sxs-lookup"><span data-stu-id="1ea1d-146">Remarks</span></span>

<span data-ttu-id="1ea1d-147">此函数包装对的调用[FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))函数。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ea1d-148">要求</span><span class="sxs-lookup"><span data-stu-id="1ea1d-148">Requirements</span></span>

 <span data-ttu-id="1ea1d-149">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea1d-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1ea1d-150">**库：** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="1ea1d-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="1ea1d-151">**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea1d-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ea1d-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ea1d-152">See also</span></span>

- [<span data-ttu-id="1ea1d-153">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="1ea1d-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
