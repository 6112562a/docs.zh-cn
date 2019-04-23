---
title: GetAssemblyRefHash 方法
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fa8d42f9e849db6a02f6c62b37e04cf5dee016e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119647"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="1fadc-102">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="1fadc-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="1fadc-103">检索给定程序集哈希 blob。</span><span class="sxs-lookup"><span data-stu-id="1fadc-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fadc-104">语法</span><span class="sxs-lookup"><span data-stu-id="1fadc-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fadc-105">参数</span><span class="sxs-lookup"><span data-stu-id="1fadc-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="1fadc-106">哈希将引用的程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="1fadc-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="1fadc-107">接收生成的哈希 blob。</span><span class="sxs-lookup"><span data-stu-id="1fadc-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="1fadc-108">接收大小，以字节为单位的哈希 blob。</span><span class="sxs-lookup"><span data-stu-id="1fadc-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fadc-109">返回值</span><span class="sxs-lookup"><span data-stu-id="1fadc-109">Return Value</span></span>  
 <span data-ttu-id="1fadc-110">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1fadc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fadc-111">要求</span><span class="sxs-lookup"><span data-stu-id="1fadc-111">Requirements</span></span>  
 <span data-ttu-id="1fadc-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="1fadc-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fadc-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="1fadc-113">See also</span></span>

- [<span data-ttu-id="1fadc-114">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="1fadc-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1fadc-115">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="1fadc-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1fadc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="1fadc-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
