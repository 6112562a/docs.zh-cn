---
title: CorParamAttr 枚举
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: 1d58c8c0413346536c3e61e67ca0077c08c2b387
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436487"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="4d2f5-102">CorParamAttr 枚举</span><span class="sxs-lookup"><span data-stu-id="4d2f5-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="4d2f5-103">包含一些值，用于描述方法参数的元数据。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2f5-104">语法</span><span class="sxs-lookup"><span data-stu-id="4d2f5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="4d2f5-105">Members</span><span class="sxs-lookup"><span data-stu-id="4d2f5-105">Members</span></span>  
  
|<span data-ttu-id="4d2f5-106">成员</span><span class="sxs-lookup"><span data-stu-id="4d2f5-106">Member</span></span>|<span data-ttu-id="4d2f5-107">说明</span><span class="sxs-lookup"><span data-stu-id="4d2f5-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="4d2f5-108">指定将参数传递给方法调用。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="4d2f5-109">指定从方法返回传递参数。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="4d2f5-110">指定参数为可选。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="4d2f5-111">保留供公共语言运行时内部使用。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="4d2f5-112">指定参数具有默认值。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="4d2f5-113">指定参数具有封送处理信息。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="4d2f5-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d2f5-115">要求</span><span class="sxs-lookup"><span data-stu-id="4d2f5-115">Requirements</span></span>  
 <span data-ttu-id="4d2f5-116">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2f5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d2f5-117">**标头：** Corhdr。h</span><span class="sxs-lookup"><span data-stu-id="4d2f5-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4d2f5-118">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d2f5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2f5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d2f5-119">See also</span></span>

- [<span data-ttu-id="4d2f5-120">Metadata 枚举</span><span class="sxs-lookup"><span data-stu-id="4d2f5-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
