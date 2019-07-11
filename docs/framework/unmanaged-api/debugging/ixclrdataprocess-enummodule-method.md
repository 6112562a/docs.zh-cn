---
title: IXCLRDataProcess::EnumModule 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769586"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="5a47a-102">IXCLRDataProcess::EnumModule 方法</span><span class="sxs-lookup"><span data-stu-id="5a47a-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="5a47a-103">枚举此进程的模块。</span><span class="sxs-lookup"><span data-stu-id="5a47a-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5a47a-104">语法</span><span class="sxs-lookup"><span data-stu-id="5a47a-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="5a47a-105">参数</span><span class="sxs-lookup"><span data-stu-id="5a47a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="5a47a-106">[in、 out]枚举模块句柄。</span><span class="sxs-lookup"><span data-stu-id="5a47a-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="5a47a-107">[out]枚举的模块。</span><span class="sxs-lookup"><span data-stu-id="5a47a-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a47a-108">备注</span><span class="sxs-lookup"><span data-stu-id="5a47a-108">Remarks</span></span>

<span data-ttu-id="5a47a-109">提供的方法属于`IXCLRDataProcess`接口，并对应于虚拟方法表 25 槽。</span><span class="sxs-lookup"><span data-stu-id="5a47a-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a47a-110">要求</span><span class="sxs-lookup"><span data-stu-id="5a47a-110">Requirements</span></span>

<span data-ttu-id="5a47a-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a47a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5a47a-112">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="5a47a-112">**Header:** None</span></span>  
<span data-ttu-id="5a47a-113">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="5a47a-113">**Library:** None</span></span>  
<span data-ttu-id="5a47a-114">**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5a47a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5a47a-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="5a47a-115">See also</span></span>

- [<span data-ttu-id="5a47a-116">CLRDataSourceType 枚举</span><span class="sxs-lookup"><span data-stu-id="5a47a-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5a47a-117">调试</span><span class="sxs-lookup"><span data-stu-id="5a47a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="5a47a-118">IXCLRDataModule 接口</span><span class="sxs-lookup"><span data-stu-id="5a47a-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="5a47a-119">IXCLRDataProcess 接口</span><span class="sxs-lookup"><span data-stu-id="5a47a-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
