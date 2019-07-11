---
title: FreeWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 75aec187452e2f9f442a5d4856fe6777c03f34c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741979"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="9846b-102">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="9846b-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="9846b-103">释放的 Win32 资源 blob 和关联的资源。</span><span class="sxs-lookup"><span data-stu-id="9846b-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9846b-104">语法</span><span class="sxs-lookup"><span data-stu-id="9846b-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9846b-105">参数</span><span class="sxs-lookup"><span data-stu-id="9846b-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="9846b-106">要释放的资源 blob。</span><span class="sxs-lookup"><span data-stu-id="9846b-106">The resource blob to be released.</span></span> <span data-ttu-id="9846b-107">此方法将 blob 指针分配为 NULL。</span><span class="sxs-lookup"><span data-stu-id="9846b-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9846b-108">返回值</span><span class="sxs-lookup"><span data-stu-id="9846b-108">Return Value</span></span>  
 <span data-ttu-id="9846b-109">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9846b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9846b-110">要求</span><span class="sxs-lookup"><span data-stu-id="9846b-110">Requirements</span></span>  
 <span data-ttu-id="9846b-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="9846b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9846b-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="9846b-112">See also</span></span>

- [<span data-ttu-id="9846b-113">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="9846b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9846b-114">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="9846b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9846b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="9846b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
