---
title: 合成全局静态函数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697714"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="b767c-102">合成全局静态函数</span><span class="sxs-lookup"><span data-stu-id="b767c-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="b767c-103">本部分描述合成 API 使用的非托管全局静态函数。</span><span class="sxs-lookup"><span data-stu-id="b767c-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b767c-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="b767c-104">In This Section</span></span>  
 [<span data-ttu-id="b767c-105">ClearDownloadCache 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="b767c-106">清除下载的程序集的全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="b767c-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="b767c-107">CompareAssemblyIdentity 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="b767c-108">比较两个程序集标识，以确定它们是否等效。</span><span class="sxs-lookup"><span data-stu-id="b767c-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="b767c-109">CreateApplicationContext 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="b767c-110">仅供内部使用。</span><span class="sxs-lookup"><span data-stu-id="b767c-110">Internal only.</span></span> <span data-ttu-id="b767c-111">（此函数支持.NET Framework 基础结构，不应在代码中直接使用。）</span><span class="sxs-lookup"><span data-stu-id="b767c-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="b767c-112">CreateAssemblyCache 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="b767c-113">获取一个指向到新[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)实例，它表示全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="b767c-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b767c-114">CreateAssemblyEnum 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="b767c-115">获取一个指向[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)实例，它表示位于指定的程序集的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="b767c-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="b767c-116">CreateAssemblyNameObject 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="b767c-117">获取一个指向[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)实例，它表示具有指定名称的程序集的唯一标识。</span><span class="sxs-lookup"><span data-stu-id="b767c-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="b767c-118">CreateHistoryReader 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="b767c-119">创建指定的文件的历史记录读取。</span><span class="sxs-lookup"><span data-stu-id="b767c-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="b767c-120">CreateInstallReferenceEnum 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="b767c-121">获取一个指向[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)实例，它表示对指定的程序集的应用程序的引用的列表。</span><span class="sxs-lookup"><span data-stu-id="b767c-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="b767c-122">GetAppIdAuthority 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="b767c-123">获取一个指向[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理密钥的应用程序标识和引用的实例。</span><span class="sxs-lookup"><span data-stu-id="b767c-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="b767c-124">GetAssemblyIdentityFromFile 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="b767c-125">获取一个指向`IUnknown`对象具有指定`IID`中程序集在指定的文件路径。</span><span class="sxs-lookup"><span data-stu-id="b767c-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="b767c-126">GetCachePath 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="b767c-127">获取使用指定的标志的缓存程序集的路径。</span><span class="sxs-lookup"><span data-stu-id="b767c-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="b767c-128">GetHistoryFileDirectory 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="b767c-129">检索应用程序历史记录目录的路径。</span><span class="sxs-lookup"><span data-stu-id="b767c-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="b767c-130">GetIdentityAuthority 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="b767c-131">获取一个指向[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理密钥的代码对象的实例。</span><span class="sxs-lookup"><span data-stu-id="b767c-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="b767c-132">IsFrameworkAssembly 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="b767c-133">获取一个值，该值指示指定的程序集是否已托管。</span><span class="sxs-lookup"><span data-stu-id="b767c-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="b767c-134">NukeDownloadedCache 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="b767c-135">删除公共语言运行时下载缓存。</span><span class="sxs-lookup"><span data-stu-id="b767c-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="b767c-136">PreBindAssemblyEx 函数</span><span class="sxs-lookup"><span data-stu-id="b767c-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="b767c-137">获取程序集的策略后的显示名称。</span><span class="sxs-lookup"><span data-stu-id="b767c-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b767c-138">相关章节</span><span class="sxs-lookup"><span data-stu-id="b767c-138">Related Sections</span></span>  
 [<span data-ttu-id="b767c-139">合成接口</span><span class="sxs-lookup"><span data-stu-id="b767c-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="b767c-140">合成枚举</span><span class="sxs-lookup"><span data-stu-id="b767c-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="b767c-141">合成结构</span><span class="sxs-lookup"><span data-stu-id="b767c-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="b767c-142">全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="b767c-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
