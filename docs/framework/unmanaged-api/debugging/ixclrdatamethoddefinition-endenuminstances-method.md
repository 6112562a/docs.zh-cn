---
title: IXCLRDataMethodDefinition::EndEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3d9e3ca31eddff9d08607c4d6d37ca76139bf5d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756305"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="b5fb2-102">IXCLRDataMethodDefinition::EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="b5fb2-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="b5fb2-103">释放使用的内部实例枚举过程中使用的迭代器的资源。</span><span class="sxs-lookup"><span data-stu-id="b5fb2-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b5fb2-104">语法</span><span class="sxs-lookup"><span data-stu-id="b5fb2-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="b5fb2-105">参数</span><span class="sxs-lookup"><span data-stu-id="b5fb2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b5fb2-106">[out]枚举的实例句柄。</span><span class="sxs-lookup"><span data-stu-id="b5fb2-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5fb2-107">备注</span><span class="sxs-lookup"><span data-stu-id="b5fb2-107">Remarks</span></span>

<span data-ttu-id="b5fb2-108">提供的方法属于`IXCLRDataMethodDefinition`接口，并对应于虚拟方法表的第五个槽。</span><span class="sxs-lookup"><span data-stu-id="b5fb2-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5fb2-109">要求</span><span class="sxs-lookup"><span data-stu-id="b5fb2-109">Requirements</span></span>

<span data-ttu-id="b5fb2-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fb2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b5fb2-111">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="b5fb2-111">**Header:** None</span></span>  
<span data-ttu-id="b5fb2-112">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="b5fb2-112">**Library:** None</span></span>  
<span data-ttu-id="b5fb2-113">**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b5fb2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b5fb2-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="b5fb2-114">See also</span></span>

- [<span data-ttu-id="b5fb2-115">调试</span><span class="sxs-lookup"><span data-stu-id="b5fb2-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b5fb2-116">IXCLRDataMethodDefinition 接口</span><span class="sxs-lookup"><span data-stu-id="b5fb2-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
