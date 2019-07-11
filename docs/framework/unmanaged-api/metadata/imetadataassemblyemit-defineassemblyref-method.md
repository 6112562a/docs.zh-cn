---
title: IMetaDataAssemblyEmit::DefineAssemblyRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c150f4bda901627fc21ed54926c3cf959bb829a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776301"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="c2186-102">IMetaDataAssemblyEmit::DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="c2186-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="c2186-103">创建包含此程序集引用的程序集的元数据的 `AssemblyRef` 结构，并返回关联的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="c2186-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2186-104">语法</span><span class="sxs-lookup"><span data-stu-id="c2186-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2186-105">参数</span><span class="sxs-lookup"><span data-stu-id="c2186-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="c2186-106">[in]引用的程序集的发布服务器的公钥。</span><span class="sxs-lookup"><span data-stu-id="c2186-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="c2186-107">帮助器函数[StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)可用于获取要将作为此参数传递的公钥的哈希。</span><span class="sxs-lookup"><span data-stu-id="c2186-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="c2186-108">[in]以字节为单位的大小`pbPublicKeyOrToken`。</span><span class="sxs-lookup"><span data-stu-id="c2186-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="c2186-109">[in]用户可读文本的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="c2186-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="c2186-110">此值不得超过 1024年个字符。</span><span class="sxs-lookup"><span data-stu-id="c2186-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c2186-111">[in]ASSEMBLYMETADATA 实例包含引用的程序集的版本、 平台和区域设置信息。</span><span class="sxs-lookup"><span data-stu-id="c2186-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c2186-112">[in]与引用的程序集关联的哈希数据。</span><span class="sxs-lookup"><span data-stu-id="c2186-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="c2186-113">可选。</span><span class="sxs-lookup"><span data-stu-id="c2186-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c2186-114">[in]以字节为单位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="c2186-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="c2186-115">[in]按位组合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)影响执行引擎的行为的值。</span><span class="sxs-lookup"><span data-stu-id="c2186-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="c2186-116">[out]指向返回的指针`AssemblyRef`元数据标记。</span><span class="sxs-lookup"><span data-stu-id="c2186-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2186-117">备注</span><span class="sxs-lookup"><span data-stu-id="c2186-117">Remarks</span></span>  
 <span data-ttu-id="c2186-118">一个`AssemblyRef`必须为此程序集引用每个程序集定义元数据结构。</span><span class="sxs-lookup"><span data-stu-id="c2186-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="c2186-119">在运行时，引用的程序集的详细信息将传递给它们表示"按生成"信息指示的程序集冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="c2186-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="c2186-120">程序集解析程序然后将策略应用。</span><span class="sxs-lookup"><span data-stu-id="c2186-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2186-121">要求</span><span class="sxs-lookup"><span data-stu-id="c2186-121">Requirements</span></span>  
 <span data-ttu-id="c2186-122">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2186-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2186-123">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c2186-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2186-124">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="c2186-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2186-125">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2186-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2186-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="c2186-126">See also</span></span>

- [<span data-ttu-id="c2186-127">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="c2186-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
