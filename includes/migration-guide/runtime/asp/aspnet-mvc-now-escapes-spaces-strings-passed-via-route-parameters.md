---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803224"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="9f858-101">ASP.NET MVC 现在将转义通过路由参数传递的字符串中的空格</span><span class="sxs-lookup"><span data-stu-id="9f858-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9f858-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9f858-102">Details</span></span>|<span data-ttu-id="9f858-103">为了遵守 RFC 2396，从路由中填充操作参数时，现在将转义路由路径中的空格。</span><span class="sxs-lookup"><span data-stu-id="9f858-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="9f858-104">因此，尽管 <code>/controller/action/some data</code> 之前会匹配路由 <code>/controller/action/{data}</code> 并提供 <code>some data</code> 作为数据参数，但它现在将改为提供 <code>some%20data</code>。</span><span class="sxs-lookup"><span data-stu-id="9f858-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="9f858-105">建议</span><span class="sxs-lookup"><span data-stu-id="9f858-105">Suggestion</span></span>|<span data-ttu-id="9f858-106">应更新代码，以取消转义路由中的字符串参数。</span><span class="sxs-lookup"><span data-stu-id="9f858-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="9f858-107">如果需要原始 URI，可通过 <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API 进行访问。</span><span class="sxs-lookup"><span data-stu-id="9f858-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="9f858-108">范围</span><span class="sxs-lookup"><span data-stu-id="9f858-108">Scope</span></span>|<span data-ttu-id="9f858-109">次要</span><span class="sxs-lookup"><span data-stu-id="9f858-109">Minor</span></span>|
|<span data-ttu-id="9f858-110">Version</span><span class="sxs-lookup"><span data-stu-id="9f858-110">Version</span></span>|<span data-ttu-id="9f858-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9f858-111">4.5.2</span></span>|
|<span data-ttu-id="9f858-112">类型</span><span class="sxs-lookup"><span data-stu-id="9f858-112">Type</span></span>|<span data-ttu-id="9f858-113">运行时</span><span class="sxs-lookup"><span data-stu-id="9f858-113">Runtime</span></span>|
|<span data-ttu-id="9f858-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9f858-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
