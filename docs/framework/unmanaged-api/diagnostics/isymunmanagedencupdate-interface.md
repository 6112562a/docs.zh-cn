---
title: ISymUnmanagedENCUpdate 接口
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 378322c28d59b2a6e7c09f2f2c4bf55bb019d01d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171829"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="d2da7-102">ISymUnmanagedENCUpdate 接口</span><span class="sxs-lookup"><span data-stu-id="d2da7-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="d2da7-103">为编辑并继续功能提供功能。</span><span class="sxs-lookup"><span data-stu-id="d2da7-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2da7-104">方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-104">Methods</span></span>  
  
|<span data-ttu-id="d2da7-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-105">Method</span></span>|<span data-ttu-id="d2da7-106">描述</span><span class="sxs-lookup"><span data-stu-id="d2da7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2da7-107">GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="d2da7-108">获取本地变量的数目。</span><span class="sxs-lookup"><span data-stu-id="d2da7-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="d2da7-109">GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="d2da7-110">获取本地变量。</span><span class="sxs-lookup"><span data-stu-id="d2da7-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="d2da7-111">InitializeForEnc 方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="d2da7-112">使方法边界，以在首次调用之前计算[ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d2da7-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="d2da7-113">UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="d2da7-114">允许更新的方法，已不被重新编译，但其行已独立移动的行信息。</span><span class="sxs-lookup"><span data-stu-id="d2da7-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d2da7-115">允许每个语句的增量。</span><span class="sxs-lookup"><span data-stu-id="d2da7-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="d2da7-116">UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="d2da7-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="d2da7-117">允许编译器忽略尚未修改的程序数据库 (PDB) 流中的函数，前提是行信息满足要求。</span><span class="sxs-lookup"><span data-stu-id="d2da7-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="d2da7-118">可使用旧的 PDB 行信息和函数中的所有行的一个增量确定正确的行信息。</span><span class="sxs-lookup"><span data-stu-id="d2da7-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2da7-119">要求</span><span class="sxs-lookup"><span data-stu-id="d2da7-119">Requirements</span></span>  
 <span data-ttu-id="d2da7-120">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2da7-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2da7-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="d2da7-121">See also</span></span>

- [<span data-ttu-id="d2da7-122">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="d2da7-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
