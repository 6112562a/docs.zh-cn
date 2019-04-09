---
title: ISymENCUnmanagedMethod 接口
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4474269688094ea6c81b06659727acfb9c2ad6c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095706"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="60f61-102">ISymENCUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="60f61-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="60f61-103">提供有关编辑并继续功能的信息。</span><span class="sxs-lookup"><span data-stu-id="60f61-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60f61-104">方法</span><span class="sxs-lookup"><span data-stu-id="60f61-104">Methods</span></span>  
  
|<span data-ttu-id="60f61-105">方法</span><span class="sxs-lookup"><span data-stu-id="60f61-105">Method</span></span>|<span data-ttu-id="60f61-106">描述</span><span class="sxs-lookup"><span data-stu-id="60f61-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60f61-107">GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="60f61-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="60f61-108">获取此方法中的行的文档。</span><span class="sxs-lookup"><span data-stu-id="60f61-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="60f61-109">GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="60f61-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="60f61-110">获取此方法中的行的文档数。</span><span class="sxs-lookup"><span data-stu-id="60f61-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="60f61-111">GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="60f61-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="60f61-112">获取与某一偏移量关联的行的文件名称。</span><span class="sxs-lookup"><span data-stu-id="60f61-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="60f61-113">GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="60f61-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="60f61-114">获取与某一偏移量关联的行信息。</span><span class="sxs-lookup"><span data-stu-id="60f61-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="60f61-115">GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="60f61-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="60f61-116">获取的最小起始行和方法的最大结束行中特定文档。</span><span class="sxs-lookup"><span data-stu-id="60f61-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60f61-117">要求</span><span class="sxs-lookup"><span data-stu-id="60f61-117">Requirements</span></span>  
 <span data-ttu-id="60f61-118">**标头：** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="60f61-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f61-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="60f61-119">See also</span></span>

- [<span data-ttu-id="60f61-120">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="60f61-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
