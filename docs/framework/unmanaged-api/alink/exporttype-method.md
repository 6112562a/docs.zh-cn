---
title: ExportType 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd1ec9caa70dd7016253ae4385b16dbfb982f956
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742015"
---
# <a name="exporttype-method"></a><span data-ttu-id="73793-102">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="73793-102">ExportType Method</span></span>
<span data-ttu-id="73793-103">指定的类型是可导出。</span><span class="sxs-lookup"><span data-stu-id="73793-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73793-104">语法</span><span class="sxs-lookup"><span data-stu-id="73793-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="73793-105">参数</span><span class="sxs-lookup"><span data-stu-id="73793-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="73793-106">要从导出的程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="73793-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="73793-107">定义可导出的类型的文件的文件标记或程序集 ID。</span><span class="sxs-lookup"><span data-stu-id="73793-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="73793-108">标记要成为可导出的类型。</span><span class="sxs-lookup"><span data-stu-id="73793-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="73793-109">要成为可导出的完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="73793-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="73793-110">`ComType` 标志，如`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="73793-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="73793-111">此参数可能会传递到[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="73793-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="73793-112">接收导出的类型的令牌。</span><span class="sxs-lookup"><span data-stu-id="73793-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73793-113">返回值</span><span class="sxs-lookup"><span data-stu-id="73793-113">Return Value</span></span>  
 <span data-ttu-id="73793-114">如果该方法成功，返回，则为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="73793-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73793-115">要求</span><span class="sxs-lookup"><span data-stu-id="73793-115">Requirements</span></span>  
 <span data-ttu-id="73793-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="73793-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73793-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="73793-117">See also</span></span>

- [<span data-ttu-id="73793-118">IALink 接口</span><span class="sxs-lookup"><span data-stu-id="73793-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="73793-119">IALink2 接口</span><span class="sxs-lookup"><span data-stu-id="73793-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="73793-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="73793-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
