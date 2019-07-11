---
title: IXCLRDataMethodDefinition::StartEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 89473f2a6a3da73ee5d172a3700bdb4d624278ff
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756293"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="bda71-102">IXCLRDataMethodDefinition::StartEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="bda71-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="bda71-103">提供一个句柄的方法实例枚举给定`IXCLRDataAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="bda71-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bda71-104">语法</span><span class="sxs-lookup"><span data-stu-id="bda71-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="bda71-105">参数</span><span class="sxs-lookup"><span data-stu-id="bda71-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="bda71-106">[in]枚举 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="bda71-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="bda71-107">[out]枚举的实例句柄。</span><span class="sxs-lookup"><span data-stu-id="bda71-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="bda71-108">备注</span><span class="sxs-lookup"><span data-stu-id="bda71-108">Remarks</span></span>

<span data-ttu-id="bda71-109">提供的方法属于`IXCLRDataMethodDefinition`接口，并对应于虚拟方法表的第三个槽。</span><span class="sxs-lookup"><span data-stu-id="bda71-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bda71-110">要求</span><span class="sxs-lookup"><span data-stu-id="bda71-110">Requirements</span></span>

<span data-ttu-id="bda71-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bda71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bda71-112">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="bda71-112">**Header:** None</span></span>  
<span data-ttu-id="bda71-113">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="bda71-113">**Library:** None</span></span>  
<span data-ttu-id="bda71-114">**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bda71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bda71-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="bda71-115">See also</span></span>

- [<span data-ttu-id="bda71-116">CLRDataSourceType 枚举</span><span class="sxs-lookup"><span data-stu-id="bda71-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="bda71-117">调试</span><span class="sxs-lookup"><span data-stu-id="bda71-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="bda71-118">IXCLRDataMethodDefinition 接口</span><span class="sxs-lookup"><span data-stu-id="bda71-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
