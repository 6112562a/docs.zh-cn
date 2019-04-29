---
title: EmitAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790060"
---
# <a name="emitassembly-method"></a><span data-ttu-id="a441a-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="a441a-102">EmitAssembly Method</span></span>
<span data-ttu-id="a441a-103">创建程序集。</span><span class="sxs-lookup"><span data-stu-id="a441a-103">Creates the assembly.</span></span> <span data-ttu-id="a441a-104">所有其他文件关闭除程序集文件后，请调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a441a-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="a441a-105">生成未绑定的模块时，请勿调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a441a-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a441a-106">语法</span><span class="sxs-lookup"><span data-stu-id="a441a-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a441a-107">参数</span><span class="sxs-lookup"><span data-stu-id="a441a-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a441a-108">程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="a441a-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a441a-109">返回值</span><span class="sxs-lookup"><span data-stu-id="a441a-109">Return Value</span></span>  
 <span data-ttu-id="a441a-110">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a441a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a441a-111">要求</span><span class="sxs-lookup"><span data-stu-id="a441a-111">Requirements</span></span>  
 <span data-ttu-id="a441a-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="a441a-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a441a-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="a441a-113">See also</span></span>

- [<span data-ttu-id="a441a-114">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="a441a-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a441a-115">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="a441a-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a441a-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="a441a-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
