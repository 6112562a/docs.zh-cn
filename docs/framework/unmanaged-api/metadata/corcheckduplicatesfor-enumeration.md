---
title: CorCheckDuplicatesFor 枚举
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074867"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="e038e-102">CorCheckDuplicatesFor 枚举</span><span class="sxs-lookup"><span data-stu-id="e038e-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="e038e-103">指定将检查有重复项的元数据令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e038e-104">语法</span><span class="sxs-lookup"><span data-stu-id="e038e-104">Syntax</span></span>  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="e038e-105">成员</span><span class="sxs-lookup"><span data-stu-id="e038e-105">Members</span></span>  
  
|<span data-ttu-id="e038e-106">成员</span><span class="sxs-lookup"><span data-stu-id="e038e-106">Member</span></span>|<span data-ttu-id="e038e-107">描述</span><span class="sxs-lookup"><span data-stu-id="e038e-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="e038e-108">检查有重复项的所有元数据标记。</span><span class="sxs-lookup"><span data-stu-id="e038e-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="e038e-109">未使用。</span><span class="sxs-lookup"><span data-stu-id="e038e-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="e038e-110">不会检查有重复项的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="e038e-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="e038e-111">检查重复项的`mdTypeDef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="e038e-112">检查重复项的`mdInterfaceImpl`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="e038e-113">检查重复项的`mdMethodDef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="e038e-114">检查重复项的`mdTypeRef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="e038e-115">检查重复项的`mdMemberRef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="e038e-116">检查重复项的`mdCustomAttribute`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="e038e-117">检查重复项的`mdParamDef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="e038e-118">检查重复项的`mdPermission`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="e038e-119">检查重复项的`mdProperty`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="e038e-120">检查重复项的`mdEvent`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="e038e-121">检查重复项的`mdFieldDef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="e038e-122">检查重复项的`mdSignature`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="e038e-123">检查重复项的`mdModuleRef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="e038e-124">检查重复项的`mdTypeSpec`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="e038e-125">检查重复项的`mdImplMap`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="e038e-126">检查重复项的`mdAssemblyRef`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="e038e-127">检查重复项的`mdFile`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="e038e-128">检查重复项的`mdExportedType`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="e038e-129">检查重复项的`mdManifestResource`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="e038e-130">检查重复项的`mdGenericParam`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="e038e-131">检查重复项的`mdMethodSpec`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="e038e-132">检查重复项的`mdGenericParamConstraint`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="e038e-133">检查重复项的`mdAssembly`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="e038e-134">检查重复的项`mdMemberRef`， `mdTypeRef`， `mdSignature`， `mdTypeSpec`，和`mdMethodSpec`令牌。</span><span class="sxs-lookup"><span data-stu-id="e038e-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e038e-135">要求</span><span class="sxs-lookup"><span data-stu-id="e038e-135">Requirements</span></span>  
 <span data-ttu-id="e038e-136">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e038e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e038e-137">**标头：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e038e-137">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="e038e-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e038e-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e038e-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="e038e-139">See also</span></span>

- [<span data-ttu-id="e038e-140">元数据枚举</span><span class="sxs-lookup"><span data-stu-id="e038e-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
