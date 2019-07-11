---
title: ImportFile2 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1193af7b7375dfd3367c12fdb0067c9c30c614f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741748"
---
# <a name="importfile2-method"></a><span data-ttu-id="116b3-102">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="116b3-102">ImportFile2 Method</span></span>
<span data-ttu-id="116b3-103">导入程序集和未绑定的模块。</span><span class="sxs-lookup"><span data-stu-id="116b3-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="116b3-104">此方法就像[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但仍可正常工作磁盘上不存在要导入的文件。</span><span class="sxs-lookup"><span data-stu-id="116b3-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116b3-105">语法</span><span class="sxs-lookup"><span data-stu-id="116b3-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="116b3-106">参数</span><span class="sxs-lookup"><span data-stu-id="116b3-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="116b3-107">要导入文件的名称。</span><span class="sxs-lookup"><span data-stu-id="116b3-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="116b3-108">可用于重命名该文件并将其链接到该程序集的可选的输出文件名称。</span><span class="sxs-lookup"><span data-stu-id="116b3-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="116b3-109">可选的作用域[IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="116b3-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="116b3-110">如果为 TRUE，则使用 ImportTypes 时，必须手动执行否则导入。</span><span class="sxs-lookup"><span data-stu-id="116b3-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="116b3-111">接收文件或程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="116b3-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="116b3-112">接收[IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="116b3-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="116b3-113">如果该文件不是程序集为 NULL。</span><span class="sxs-lookup"><span data-stu-id="116b3-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="116b3-114">接收找到的文件和/或导入的作用域。</span><span class="sxs-lookup"><span data-stu-id="116b3-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="116b3-115">返回值</span><span class="sxs-lookup"><span data-stu-id="116b3-115">Return Value</span></span>  
 <span data-ttu-id="116b3-116">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="116b3-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="116b3-117">要求</span><span class="sxs-lookup"><span data-stu-id="116b3-117">Requirements</span></span>  
 <span data-ttu-id="116b3-118">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="116b3-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116b3-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="116b3-119">See also</span></span>

- [<span data-ttu-id="116b3-120">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="116b3-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="116b3-121">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="116b3-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="116b3-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="116b3-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
