---
title: OSINFO 结构
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a36cd3c5fb638799a735e4b4a1a98959500300b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761596"
---
# <a name="osinfo-structure"></a><span data-ttu-id="b1aa9-102">OSINFO 结构</span><span class="sxs-lookup"><span data-stu-id="b1aa9-102">OSINFO Structure</span></span>
<span data-ttu-id="b1aa9-103">包含有关操作系统的程序集或模块的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1aa9-104">语法</span><span class="sxs-lookup"><span data-stu-id="b1aa9-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b1aa9-105">成员</span><span class="sxs-lookup"><span data-stu-id="b1aa9-105">Members</span></span>  
  
|<span data-ttu-id="b1aa9-106">成员</span><span class="sxs-lookup"><span data-stu-id="b1aa9-106">Member</span></span>|<span data-ttu-id="b1aa9-107">描述</span><span class="sxs-lookup"><span data-stu-id="b1aa9-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="b1aa9-108">一个由 Microsoft Windows 平台函数定义的标识符值`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="b1aa9-109">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="b1aa9-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="b1aa9-110">-VER_PLATFORM_WIN32s 或 0x0000，指定 Microsoft Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="b1aa9-111">-VER_PLATFORM_WIN32_WINDOWS 或从 0x0001，以指定 Windows 95 和 Windows 98 或继承自此它们的操作系统。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="b1aa9-112">-VER_PLATFORM_WIN32_NT 或 0x0010，若要指定 Windows NT 或继承自它的操作系统。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="b1aa9-113">操作系统主版本或 NULL 值，以指示任何版本。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="b1aa9-114">操作系统次版本或 NULL 值，以指示任何版本。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1aa9-115">备注</span><span class="sxs-lookup"><span data-stu-id="b1aa9-115">Remarks</span></span>  
 <span data-ttu-id="b1aa9-116">`OSINFO` 基于`OSVERSIONINFOEX`结构，它是 Microsoft Windows 平台函数调用中使用的`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="b1aa9-117">ASSEMBLYMETADATA 结构使用此结构以指示其操作系统的支持。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1aa9-118">要求</span><span class="sxs-lookup"><span data-stu-id="b1aa9-118">Requirements</span></span>  
 <span data-ttu-id="b1aa9-119">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1aa9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1aa9-120">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1aa9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1aa9-121">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="b1aa9-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1aa9-122">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1aa9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1aa9-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1aa9-123">See also</span></span>

- [<span data-ttu-id="b1aa9-124">元数据结构</span><span class="sxs-lookup"><span data-stu-id="b1aa9-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="b1aa9-125">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="b1aa9-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
