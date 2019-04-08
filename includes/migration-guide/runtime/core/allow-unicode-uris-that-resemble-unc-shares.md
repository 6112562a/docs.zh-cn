---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760714"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="474bc-101">允许在类似于 UNC 共享的 URI 中使用 Unicode</span><span class="sxs-lookup"><span data-stu-id="474bc-101">Allow Unicode in URIs that resemble UNC shares</span></span>

|   |   |
|---|---|
|<span data-ttu-id="474bc-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="474bc-102">Details</span></span>|<span data-ttu-id="474bc-103">在 <xref:System.Uri?displayProperty=fullName> 中，构造包含 UNC 共享名称和 Unicode 字符的文件 URI 将不再导致出现内部状态无效的 URI。</span><span class="sxs-lookup"><span data-stu-id="474bc-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="474bc-104">仅当以下各项均为 true 时，该行为才会更改：</span><span class="sxs-lookup"><span data-stu-id="474bc-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="474bc-105">URI 具有方案 <code>file:</code>，且后接四个及以上的斜杠。</span><span class="sxs-lookup"><span data-stu-id="474bc-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="474bc-106">主机名称以下划线或其他非保留符号开头。</span><span class="sxs-lookup"><span data-stu-id="474bc-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="474bc-107">URI 包含 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="474bc-107">The URI contains Unicode characters.</span></span></li></ul>|
|<span data-ttu-id="474bc-108">建议</span><span class="sxs-lookup"><span data-stu-id="474bc-108">Suggestion</span></span>|<span data-ttu-id="474bc-109">使用始终包含 Unicode 的 URI 的应用程序可能已使用此行为来禁止对 UNC 共享的引用。</span><span class="sxs-lookup"><span data-stu-id="474bc-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="474bc-110">这些应用程序应使用 <xref:System.Uri.IsUnc>。</span><span class="sxs-lookup"><span data-stu-id="474bc-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>|
|<span data-ttu-id="474bc-111">范围</span><span class="sxs-lookup"><span data-stu-id="474bc-111">Scope</span></span>|<span data-ttu-id="474bc-112">边缘</span><span class="sxs-lookup"><span data-stu-id="474bc-112">Edge</span></span>|
|<span data-ttu-id="474bc-113">版本</span><span class="sxs-lookup"><span data-stu-id="474bc-113">Version</span></span>|<span data-ttu-id="474bc-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="474bc-114">4.7.2</span></span>|
|<span data-ttu-id="474bc-115">类型</span><span class="sxs-lookup"><span data-stu-id="474bc-115">Type</span></span>|<span data-ttu-id="474bc-116">运行时</span><span class="sxs-lookup"><span data-stu-id="474bc-116">Runtime</span></span>|
|<span data-ttu-id="474bc-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="474bc-117">Affected APIs</span></span>|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

