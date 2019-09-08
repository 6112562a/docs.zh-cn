---
title: EmitAssemblyCustomAttribute 方法
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777437"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="56f62-102">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="56f62-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="56f62-103">调用以设置程序集级别的自定义特性。</span><span class="sxs-lookup"><span data-stu-id="56f62-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f62-104">语法</span><span class="sxs-lookup"><span data-stu-id="56f62-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="56f62-105">参数</span><span class="sxs-lookup"><span data-stu-id="56f62-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="56f62-106">程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="56f62-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="56f62-107">定义属性的文件。</span><span class="sxs-lookup"><span data-stu-id="56f62-107">File that defiles the attribute.</span></span> <span data-ttu-id="56f62-108">如果不指示未`AssemblyID`绑定的 .netmodule，则可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="56f62-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="56f62-109">自定义属性的类型。</span><span class="sxs-lookup"><span data-stu-id="56f62-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="56f62-110">自定义值数据。</span><span class="sxs-lookup"><span data-stu-id="56f62-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="56f62-111">自定义值数据的长度。</span><span class="sxs-lookup"><span data-stu-id="56f62-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="56f62-112">如果自定义属性与程序集签名相关，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="56f62-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="56f62-113">如果要发出多个属性，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="56f62-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56f62-114">返回值</span><span class="sxs-lookup"><span data-stu-id="56f62-114">Return Value</span></span>  
 <span data-ttu-id="56f62-115">如果该方法成功，则返回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="56f62-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f62-116">要求</span><span class="sxs-lookup"><span data-stu-id="56f62-116">Requirements</span></span>  
 <span data-ttu-id="56f62-117">需要 alink</span><span class="sxs-lookup"><span data-stu-id="56f62-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f62-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="56f62-118">See also</span></span>

- [<span data-ttu-id="56f62-119">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="56f62-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="56f62-120">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="56f62-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="56f62-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="56f62-121">ALink API</span></span>](index.md)
