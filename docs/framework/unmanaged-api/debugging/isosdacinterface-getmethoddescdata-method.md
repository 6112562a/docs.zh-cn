---
title: ISOSDacInterface::GetMethodDescData 方法
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ea54fdd83b9470db4a08daceaa695e450f5ca1af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764820"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="d7e76-102">ISOSDacInterface::GetMethodDescData 方法</span><span class="sxs-lookup"><span data-stu-id="d7e76-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="d7e76-103">获取给定 MethodDesc 指针的数据。</span><span class="sxs-lookup"><span data-stu-id="d7e76-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d7e76-104">语法</span><span class="sxs-lookup"><span data-stu-id="d7e76-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="d7e76-105">参数</span><span class="sxs-lookup"><span data-stu-id="d7e76-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="d7e76-106">[in]MethodDesc 的地址。</span><span class="sxs-lookup"><span data-stu-id="d7e76-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="d7e76-107">[in]该方法的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d7e76-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="d7e76-108">[out]返回从内部 Api 与 MethodDesc 关联的数据。</span><span class="sxs-lookup"><span data-stu-id="d7e76-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="d7e76-109">[out]已还原的 rejit 版本数。</span><span class="sxs-lookup"><span data-stu-id="d7e76-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="d7e76-110">[out]返回从内部 Api 与已还原的 rejit 版本关联的数据。</span><span class="sxs-lookup"><span data-stu-id="d7e76-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="d7e76-111">[out]存储与已还原的 ReJit 版本关联的数据所需的字节数。</span><span class="sxs-lookup"><span data-stu-id="d7e76-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7e76-112">备注</span><span class="sxs-lookup"><span data-stu-id="d7e76-112">Remarks</span></span>

<span data-ttu-id="d7e76-113">提供的方法属于`ISOSDacInterface`接口，并对应于虚拟方法表的 20 槽。</span><span class="sxs-lookup"><span data-stu-id="d7e76-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="d7e76-114">若要能够使用它们[ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md)必须定义为 64 位无符号整数。</span><span class="sxs-lookup"><span data-stu-id="d7e76-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7e76-115">要求</span><span class="sxs-lookup"><span data-stu-id="d7e76-115">Requirements</span></span>

<span data-ttu-id="d7e76-116">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7e76-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d7e76-117">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="d7e76-117">**Header:** None</span></span>  
<span data-ttu-id="d7e76-118">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="d7e76-118">**Library:** None</span></span>  
<span data-ttu-id="d7e76-119">**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e76-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d7e76-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7e76-120">See also</span></span>

- [<span data-ttu-id="d7e76-121">调试</span><span class="sxs-lookup"><span data-stu-id="d7e76-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="d7e76-122">ISOSDacInterface 接口</span><span class="sxs-lookup"><span data-stu-id="d7e76-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
