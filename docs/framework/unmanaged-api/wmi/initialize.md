---
title: Initialize 函数（非托管 API 参考）
description: Initialize 函数执行 WMI 初始化。
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127396"
---
# <a name="initialize-function"></a><span data-ttu-id="b3184-103">Initialize 函数</span><span class="sxs-lookup"><span data-stu-id="b3184-103">Initialize function</span></span>

<span data-ttu-id="b3184-104">执行 WMI 初始化。</span><span class="sxs-lookup"><span data-stu-id="b3184-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b3184-105">语法</span><span class="sxs-lookup"><span data-stu-id="b3184-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="b3184-106">参数</span><span class="sxs-lookup"><span data-stu-id="b3184-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="b3184-107">[in] `true` 以指示允许调用 WMI 对象上的 QueryInterface;否则 `false`。</span><span class="sxs-lookup"><span data-stu-id="b3184-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="b3184-108">返回值</span><span class="sxs-lookup"><span data-stu-id="b3184-108">Return value</span></span>

<span data-ttu-id="b3184-109">函数始终返回 `S_OK` （0）。</span><span class="sxs-lookup"><span data-stu-id="b3184-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="b3184-110">要求</span><span class="sxs-lookup"><span data-stu-id="b3184-110">Requirements</span></span>

<span data-ttu-id="b3184-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3184-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b3184-112">**标头：** WMINet_Utils</span><span class="sxs-lookup"><span data-stu-id="b3184-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="b3184-113">**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3184-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b3184-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="b3184-114">See also</span></span>

- [<span data-ttu-id="b3184-115">WMI 和性能计数器（非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="b3184-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
