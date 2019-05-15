---
title: EndEnumeration 函数 （非托管 API 参考）
description: EndEnumeration 函数终止枚举。
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5c576cb808ee92452c193c3fbce4f1d2c2cad05
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636770"
---
# <a name="endenumeration-function"></a><span data-ttu-id="8125d-103">EndEnumeration 函数</span><span class="sxs-lookup"><span data-stu-id="8125d-103">EndEnumeration function</span></span>

<span data-ttu-id="8125d-104">终止通过调用开始枚举序列[BeginEnumeration 函数](beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="8125d-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8125d-105">语法</span><span class="sxs-lookup"><span data-stu-id="8125d-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="8125d-106">参数</span><span class="sxs-lookup"><span data-stu-id="8125d-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="8125d-107">[in]此参数是未使用。</span><span class="sxs-lookup"><span data-stu-id="8125d-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="8125d-108">[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。</span><span class="sxs-lookup"><span data-stu-id="8125d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="8125d-109">返回值</span><span class="sxs-lookup"><span data-stu-id="8125d-109">Return value</span></span>

<span data-ttu-id="8125d-110">此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：</span><span class="sxs-lookup"><span data-stu-id="8125d-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8125d-111">返回的常量</span><span class="sxs-lookup"><span data-stu-id="8125d-111">Constant</span></span>  |<span data-ttu-id="8125d-112">值</span><span class="sxs-lookup"><span data-stu-id="8125d-112">Value</span></span>  |<span data-ttu-id="8125d-113">描述</span><span class="sxs-lookup"><span data-stu-id="8125d-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8125d-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8125d-114">0x80041001</span></span> | <span data-ttu-id="8125d-115">已存在时的常见错误。</span><span class="sxs-lookup"><span data-stu-id="8125d-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8125d-116">0</span><span class="sxs-lookup"><span data-stu-id="8125d-116">0</span></span> | <span data-ttu-id="8125d-117">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="8125d-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8125d-118">备注</span><span class="sxs-lookup"><span data-stu-id="8125d-118">Remarks</span></span>

<span data-ttu-id="8125d-119">此函数包装对的调用[IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。</span><span class="sxs-lookup"><span data-stu-id="8125d-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="8125d-120">调用`EndEnumeration`函数不是必需的但它建议，因为它释放与枚举关联的资源。</span><span class="sxs-lookup"><span data-stu-id="8125d-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="8125d-121">但是，资源将释放自动启动下一步枚举或释放的对象时。</span><span class="sxs-lookup"><span data-stu-id="8125d-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="8125d-122">要求</span><span class="sxs-lookup"><span data-stu-id="8125d-122">Requirements</span></span>

<span data-ttu-id="8125d-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8125d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8125d-124">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8125d-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="8125d-125">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8125d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8125d-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8125d-126">See also</span></span>

- [<span data-ttu-id="8125d-127">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="8125d-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
