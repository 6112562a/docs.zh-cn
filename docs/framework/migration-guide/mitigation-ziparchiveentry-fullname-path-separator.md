---
title: 缓解：ZipArchiveEntry.FullName 路径分隔符
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457733"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="02566-102">缓解：ZipArchiveEntry.FullName 路径分隔符</span><span class="sxs-lookup"><span data-stu-id="02566-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="02566-103">自面向 .NET Framework 4.6.1 的应用起，<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 属性中使用的路径分隔符已从旧版 .NET Framework 中使用的反斜杠（“\\”）更改为正斜杠（“/”）。</span><span class="sxs-lookup"><span data-stu-id="02566-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="02566-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 对象是通过调用 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的重载之一进行创建。</span><span class="sxs-lookup"><span data-stu-id="02566-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="02566-105">影响</span><span class="sxs-lookup"><span data-stu-id="02566-105">Impact</span></span>  
 <span data-ttu-id="02566-106">该更改使 .NET 实现遵循 [.ZIP 文件格式规范](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)的 4.4.17.1 部分，还允许 .ZIP 存档在非 Windows 系统上进行解压缩。</span><span class="sxs-lookup"><span data-stu-id="02566-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="02566-107">对于定位非 Windows 操作系统（如 Macintosh）上旧版 .NET Framework 的应用程序，解压缩其创建的 zip 文件无法保留目录结构。</span><span class="sxs-lookup"><span data-stu-id="02566-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="02566-108">例如，在 Macintosh 上，应用程序创建一组文件，它们的文件名与目录路径相连，还与任何反斜杠 ("\\") 字符相连。</span><span class="sxs-lookup"><span data-stu-id="02566-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="02566-109">因此，不会保留解压缩的文件的目录结构。</span><span class="sxs-lookup"><span data-stu-id="02566-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="02566-110">对于在 Windows 操作系统上由 .NET Framework<xref:System.IO> 命名空间中的 API 解压缩的 .ZIP 文件，此更改造成的影响应该是最小的，因为这些 API 可以无缝地将正斜杠 ("/") 或反斜杠 ("\\") 处理为路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="02566-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="02566-111">缓解操作</span><span class="sxs-lookup"><span data-stu-id="02566-111">Mitigation</span></span>  
 <span data-ttu-id="02566-112">如果不需要此行为，可以在应用程序配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分中添加配置设置，从而选择禁用此行为。</span><span class="sxs-lookup"><span data-stu-id="02566-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="02566-113">下面展示了 `<runtime>` 部分和选择禁用此行为的开关。</span><span class="sxs-lookup"><span data-stu-id="02566-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="02566-114">此外，对于面向先前版本的 .NET Framework，但在 .NET Framework 4.6.1 及更高版本上运行的应用，可通过将配置设置添加到应用程序配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分中来选择启用此行为。</span><span class="sxs-lookup"><span data-stu-id="02566-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="02566-115">下面展示了 `<runtime>` 部分和选择启用此行为的开关。</span><span class="sxs-lookup"><span data-stu-id="02566-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02566-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02566-116">See also</span></span>

- [<span data-ttu-id="02566-117">重定目标更改</span><span class="sxs-lookup"><span data-stu-id="02566-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="02566-118">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="02566-118">Application compatibility</span></span>](application-compatibility.md)
