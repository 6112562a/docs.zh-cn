---
title: EnumImportTypes 方法
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448733"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="5ee97-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="5ee97-102">EnumImportTypes Method</span></span>

<span data-ttu-id="5ee97-103">Enumerates each type in each scope.</span><span class="sxs-lookup"><span data-stu-id="5ee97-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ee97-104">语法</span><span class="sxs-lookup"><span data-stu-id="5ee97-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="5ee97-105">参数</span><span class="sxs-lookup"><span data-stu-id="5ee97-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="5ee97-106">Handle for enumerator.</span><span class="sxs-lookup"><span data-stu-id="5ee97-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="5ee97-107">Maximum number of types to retrieve.</span><span class="sxs-lookup"><span data-stu-id="5ee97-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="5ee97-108">Receives type tokens, not to exceed `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="5ee97-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="5ee97-109">Receives actual number of type in `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="5ee97-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ee97-110">返回值</span><span class="sxs-lookup"><span data-stu-id="5ee97-110">Return Value</span></span>

<span data-ttu-id="5ee97-111">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="5ee97-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ee97-112">要求</span><span class="sxs-lookup"><span data-stu-id="5ee97-112">Requirements</span></span>

<span data-ttu-id="5ee97-113">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="5ee97-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="5ee97-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ee97-114">See also</span></span>

- [<span data-ttu-id="5ee97-115">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="5ee97-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5ee97-116">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="5ee97-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5ee97-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="5ee97-117">ALink API</span></span>](index.md)
