---
title: SetAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741544"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="c23cb-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="c23cb-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="c23cb-103">分配要生成的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="c23cb-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="c23cb-104">不是针对生成未绑定的模块时使用。</span><span class="sxs-lookup"><span data-stu-id="c23cb-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c23cb-105">语法</span><span class="sxs-lookup"><span data-stu-id="c23cb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c23cb-106">参数</span><span class="sxs-lookup"><span data-stu-id="c23cb-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c23cb-107">清单文件的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="c23cb-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c23cb-108">指向[IMetaDataEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="c23cb-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="c23cb-109">标记中定义[AssemblyFlags 枚举](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="c23cb-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="c23cb-110">指向生成的程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="c23cb-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c23cb-111">返回值</span><span class="sxs-lookup"><span data-stu-id="c23cb-111">Return Value</span></span>  
 <span data-ttu-id="c23cb-112">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c23cb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c23cb-113">要求</span><span class="sxs-lookup"><span data-stu-id="c23cb-113">Requirements</span></span>  
 <span data-ttu-id="c23cb-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="c23cb-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23cb-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c23cb-115">See also</span></span>

- [<span data-ttu-id="c23cb-116">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="c23cb-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c23cb-117">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="c23cb-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c23cb-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="c23cb-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
