---
title: CorLocalRefPreservation 枚举
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 845994b96445d8ec2a0e37affc5164b432894a91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102188"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="cda8b-102">CorLocalRefPreservation 枚举</span><span class="sxs-lookup"><span data-stu-id="cda8b-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="cda8b-103">包含用于处理本地引用的标志值。</span><span class="sxs-lookup"><span data-stu-id="cda8b-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda8b-104">语法</span><span class="sxs-lookup"><span data-stu-id="cda8b-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="cda8b-105">成员</span><span class="sxs-lookup"><span data-stu-id="cda8b-105">Members</span></span>  
  
|<span data-ttu-id="cda8b-106">成员</span><span class="sxs-lookup"><span data-stu-id="cda8b-106">Member</span></span>|<span data-ttu-id="cda8b-107">描述</span><span class="sxs-lookup"><span data-stu-id="cda8b-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="cda8b-108">保留任何本地引用。</span><span class="sxs-lookup"><span data-stu-id="cda8b-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="cda8b-109">保留本地类型引用。</span><span class="sxs-lookup"><span data-stu-id="cda8b-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="cda8b-110">保留本地成员引用。</span><span class="sxs-lookup"><span data-stu-id="cda8b-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cda8b-111">要求</span><span class="sxs-lookup"><span data-stu-id="cda8b-111">Requirements</span></span>  
 <span data-ttu-id="cda8b-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cda8b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda8b-113">**标头：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cda8b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cda8b-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda8b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda8b-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="cda8b-115">See also</span></span>

- [<span data-ttu-id="cda8b-116">Metadata 枚举</span><span class="sxs-lookup"><span data-stu-id="cda8b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
