---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235137"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="3daba-101">ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 现在支持枚举类型</span><span class="sxs-lookup"><span data-stu-id="3daba-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3daba-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3daba-102">Details</span></span>|<span data-ttu-id="3daba-103">在 .NET Framework 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型参数 <code>T</code> 不能是枚举类型。</span><span class="sxs-lookup"><span data-stu-id="3daba-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="3daba-104">现在支持这种情况。</span><span class="sxs-lookup"><span data-stu-id="3daba-104">That scenario is now supported.</span></span>|
|<span data-ttu-id="3daba-105">建议</span><span class="sxs-lookup"><span data-stu-id="3daba-105">Suggestion</span></span>|<span data-ttu-id="3daba-106">如果在 .NET Framework 4.0 的枚举类型上调用了 Translate 或 ExecuteStoreQuery，则返回“0”。</span><span class="sxs-lookup"><span data-stu-id="3daba-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="3daba-107">如果需要该行为，调用应替换为常数 0（或其枚举等效项）。</span><span class="sxs-lookup"><span data-stu-id="3daba-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>|
|<span data-ttu-id="3daba-108">范围</span><span class="sxs-lookup"><span data-stu-id="3daba-108">Scope</span></span>|<span data-ttu-id="3daba-109">边缘</span><span class="sxs-lookup"><span data-stu-id="3daba-109">Edge</span></span>|
|<span data-ttu-id="3daba-110">版本</span><span class="sxs-lookup"><span data-stu-id="3daba-110">Version</span></span>|<span data-ttu-id="3daba-111">4.5</span><span class="sxs-lookup"><span data-stu-id="3daba-111">4.5</span></span>|
|<span data-ttu-id="3daba-112">类型</span><span class="sxs-lookup"><span data-stu-id="3daba-112">Type</span></span>|<span data-ttu-id="3daba-113">运行时</span><span class="sxs-lookup"><span data-stu-id="3daba-113">Runtime</span></span>|
|<span data-ttu-id="3daba-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3daba-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
