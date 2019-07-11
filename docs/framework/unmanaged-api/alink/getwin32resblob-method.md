---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdc1ef6490f250ebe93b0482adf244adfc0ffd56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741781"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="162e2-102">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="162e2-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="162e2-103">检索 Win32 资源 blob。</span><span class="sxs-lookup"><span data-stu-id="162e2-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="162e2-104">设置程序集选项之后调用此方法。</span><span class="sxs-lookup"><span data-stu-id="162e2-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="162e2-105">语法</span><span class="sxs-lookup"><span data-stu-id="162e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="162e2-106">参数</span><span class="sxs-lookup"><span data-stu-id="162e2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="162e2-107">程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="162e2-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="162e2-108">用于检索要构造的 Win32 版本资源时使用的文件名的文件标记</span><span class="sxs-lookup"><span data-stu-id="162e2-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="162e2-109">如果文件是 DLL，则返回 false 使 exe，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="162e2-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="162e2-110">要插入到资源 blob 的可选图标。</span><span class="sxs-lookup"><span data-stu-id="162e2-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="162e2-111">接收资源 blob。</span><span class="sxs-lookup"><span data-stu-id="162e2-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="162e2-112">接收该 blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="162e2-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="162e2-113">返回值</span><span class="sxs-lookup"><span data-stu-id="162e2-113">Return Value</span></span>  
 <span data-ttu-id="162e2-114">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="162e2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="162e2-115">要求</span><span class="sxs-lookup"><span data-stu-id="162e2-115">Requirements</span></span>  
 <span data-ttu-id="162e2-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="162e2-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162e2-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="162e2-117">See also</span></span>

- [<span data-ttu-id="162e2-118">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="162e2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="162e2-119">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="162e2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="162e2-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="162e2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
