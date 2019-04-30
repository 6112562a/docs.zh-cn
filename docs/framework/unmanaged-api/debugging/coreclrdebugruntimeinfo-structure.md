---
title: CoreClrDebugRuntimeInfo 结构
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966037"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="116cd-102">CoreClrDebugRuntimeInfo 结构</span><span class="sxs-lookup"><span data-stu-id="116cd-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="116cd-103">表示公共语言运行时 (CLR) 实例，该实例加载到远程计算机上的进程中。</span><span class="sxs-lookup"><span data-stu-id="116cd-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116cd-104">语法</span><span class="sxs-lookup"><span data-stu-id="116cd-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="116cd-105">成员</span><span class="sxs-lookup"><span data-stu-id="116cd-105">Members</span></span>  
  
|<span data-ttu-id="116cd-106">成员</span><span class="sxs-lookup"><span data-stu-id="116cd-106">Member</span></span>|<span data-ttu-id="116cd-107">描述</span><span class="sxs-lookup"><span data-stu-id="116cd-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="116cd-108">由运行在目标计算机上的远程调试代理分配的运行时标识符。</span><span class="sxs-lookup"><span data-stu-id="116cd-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="116cd-109">要求</span><span class="sxs-lookup"><span data-stu-id="116cd-109">Requirements</span></span>  
 <span data-ttu-id="116cd-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="116cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="116cd-111">**标头：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="116cd-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="116cd-112">**库：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="116cd-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="116cd-113">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="116cd-113">**.NET Framework Versions:** 3.5 SP1</span></span>
