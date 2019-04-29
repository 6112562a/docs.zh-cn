---
title: AssemblyOptions 枚举
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790099"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="9bf61-102">AssemblyOptions 枚举</span><span class="sxs-lookup"><span data-stu-id="9bf61-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="9bf61-103">枚举的程序集选项。</span><span class="sxs-lookup"><span data-stu-id="9bf61-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf61-104">语法</span><span class="sxs-lookup"><span data-stu-id="9bf61-104">Syntax</span></span>  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="9bf61-105">字段</span><span class="sxs-lookup"><span data-stu-id="9bf61-105">Fields</span></span>  
  
|<span data-ttu-id="9bf61-106">字段</span><span class="sxs-lookup"><span data-stu-id="9bf61-106">Field</span></span>|<span data-ttu-id="9bf61-107">描述</span><span class="sxs-lookup"><span data-stu-id="9bf61-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bf61-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="9bf61-108">optAssemTitle</span></span>|<span data-ttu-id="9bf61-109">字符串--表示程序集标题。</span><span class="sxs-lookup"><span data-stu-id="9bf61-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="9bf61-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="9bf61-110">optAssemDescription</span></span>|<span data-ttu-id="9bf61-111">字符串--包含程序集说明。</span><span class="sxs-lookup"><span data-stu-id="9bf61-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="9bf61-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="9bf61-112">optAssemConfig</span></span>|<span data-ttu-id="9bf61-113">字符串--包含程序集配置。</span><span class="sxs-lookup"><span data-stu-id="9bf61-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="9bf61-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="9bf61-114">optAssemOS</span></span>|<span data-ttu-id="9bf61-115">字符串-编码为:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="9bf61-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="9bf61-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="9bf61-116">optAssemProcessor</span></span>|<span data-ttu-id="9bf61-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="9bf61-117">ULONG</span></span>|  
|<span data-ttu-id="9bf61-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="9bf61-118">optAssemLocale</span></span>|<span data-ttu-id="9bf61-119">字符串--包含程序集的区域设置。</span><span class="sxs-lookup"><span data-stu-id="9bf61-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="9bf61-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="9bf61-120">optAssemVersion</span></span>|<span data-ttu-id="9bf61-121">字符串-编码为："Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="9bf61-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="9bf61-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="9bf61-122">optAssemCompany</span></span>|<span data-ttu-id="9bf61-123">字符串--包含公司。</span><span class="sxs-lookup"><span data-stu-id="9bf61-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="9bf61-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="9bf61-124">optAssemProduct</span></span>|<span data-ttu-id="9bf61-125">字符串--包含产品名称。</span><span class="sxs-lookup"><span data-stu-id="9bf61-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="9bf61-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="9bf61-126">optAssemProductVersion</span></span>|<span data-ttu-id="9bf61-127">字符串 (也称为 InformationalVersion)。</span><span class="sxs-lookup"><span data-stu-id="9bf61-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="9bf61-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="9bf61-128">optAssemCopyright</span></span>|<span data-ttu-id="9bf61-129">字符串--包含的版权信息。</span><span class="sxs-lookup"><span data-stu-id="9bf61-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="9bf61-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="9bf61-130">optAssemTrademark</span></span>|<span data-ttu-id="9bf61-131">字符串--包含商标信息。</span><span class="sxs-lookup"><span data-stu-id="9bf61-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="9bf61-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="9bf61-132">optAssemKeyFile</span></span>|<span data-ttu-id="9bf61-133">字符串 （文件名）。</span><span class="sxs-lookup"><span data-stu-id="9bf61-133">String (file name).</span></span>|  
|<span data-ttu-id="9bf61-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="9bf61-134">optAssemKeyName</span></span>|<span data-ttu-id="9bf61-135">字符串 （项名）。</span><span class="sxs-lookup"><span data-stu-id="9bf61-135">String (The key name).</span></span>|  
|<span data-ttu-id="9bf61-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="9bf61-136">optAssemAlgID</span></span>|<span data-ttu-id="9bf61-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="9bf61-137">ULONG</span></span>|  
|<span data-ttu-id="9bf61-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="9bf61-138">optAssemFlags</span></span>|<span data-ttu-id="9bf61-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="9bf61-139">ULONG</span></span>|  
|<span data-ttu-id="9bf61-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="9bf61-140">optAssemHalfSign</span></span>|<span data-ttu-id="9bf61-141">Bool （也称为 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="9bf61-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="9bf61-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="9bf61-142">optAssemFileVersion</span></span>|<span data-ttu-id="9bf61-143">字符串-编码为"Major.Minor.Build.Revision"-ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="9bf61-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="9bf61-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="9bf61-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="9bf61-145">字符串-编码为"Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="9bf61-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="9bf61-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="9bf61-146">optLastAssemOption</span></span>|<span data-ttu-id="9bf61-147">元素数的计数器。</span><span class="sxs-lookup"><span data-stu-id="9bf61-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bf61-148">要求</span><span class="sxs-lookup"><span data-stu-id="9bf61-148">Requirements</span></span>  
 <span data-ttu-id="9bf61-149">**标头：** alink.h</span><span class="sxs-lookup"><span data-stu-id="9bf61-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="9bf61-150">**库**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="9bf61-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf61-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="9bf61-151">See also</span></span>

- [<span data-ttu-id="9bf61-152">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="9bf61-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
