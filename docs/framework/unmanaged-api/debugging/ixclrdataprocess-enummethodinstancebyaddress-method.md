---
title: IXCLRDataProcess::EnumMethodInstanceByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 89b89a0cb056a0515bf0859069455a73f62aae4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769616"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="17441-102">IXCLRDataProcess::EnumMethodInstanceByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="17441-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="17441-103">枚举的方法实例的地址偏移量开始此过程。</span><span class="sxs-lookup"><span data-stu-id="17441-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="17441-104">语法</span><span class="sxs-lookup"><span data-stu-id="17441-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="17441-105">参数</span><span class="sxs-lookup"><span data-stu-id="17441-105">Parameters</span></span>

`handle`\
<span data-ttu-id="17441-106">[in]枚举的方法实例句柄。</span><span class="sxs-lookup"><span data-stu-id="17441-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="17441-107">[out]枚举的方法实例。</span><span class="sxs-lookup"><span data-stu-id="17441-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="17441-108">备注</span><span class="sxs-lookup"><span data-stu-id="17441-108">Remarks</span></span>

<span data-ttu-id="17441-109">提供的方法属于`IXCLRDataProcess`接口，并对应于虚拟方法表 28 槽。</span><span class="sxs-lookup"><span data-stu-id="17441-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="17441-110">要求</span><span class="sxs-lookup"><span data-stu-id="17441-110">Requirements</span></span>

<span data-ttu-id="17441-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17441-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="17441-112">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="17441-112">**Header:** None</span></span>   
<span data-ttu-id="17441-113">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="17441-113">**Library:** None</span></span>   
<span data-ttu-id="17441-114">**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17441-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="17441-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="17441-115">See also</span></span>

- [<span data-ttu-id="17441-116">CLRDataSourceType 枚举</span><span class="sxs-lookup"><span data-stu-id="17441-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="17441-117">调试</span><span class="sxs-lookup"><span data-stu-id="17441-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="17441-118">IXCLRDataProcess 接口</span><span class="sxs-lookup"><span data-stu-id="17441-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
