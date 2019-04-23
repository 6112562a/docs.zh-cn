---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234615"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="31c32-101">DbParameter.Precision 和 DbParameter.Scale 现在是公共虚拟成员</span><span class="sxs-lookup"><span data-stu-id="31c32-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="31c32-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="31c32-102">Details</span></span>|<span data-ttu-id="31c32-103">实现 <xref:System.Data.Common.DbParameter.Precision> 和 <xref:System.Data.Common.DbParameter.Scale> 将实现为公共虚拟属性。</span><span class="sxs-lookup"><span data-stu-id="31c32-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="31c32-104">它们替换相应的显示接口实现、<xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。</span><span class="sxs-lookup"><span data-stu-id="31c32-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="31c32-105">建议</span><span class="sxs-lookup"><span data-stu-id="31c32-105">Suggestion</span></span>|<span data-ttu-id="31c32-106">在重新生成 ADO.NET 数据库提供程序时，这些差异要求将“override”关键字应用到 Precision 和 Scale 属性。</span><span class="sxs-lookup"><span data-stu-id="31c32-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="31c32-107">仅在重新生成组件时才需要这样做；现有二进制文件将继续运行。</span><span class="sxs-lookup"><span data-stu-id="31c32-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="31c32-108">范围</span><span class="sxs-lookup"><span data-stu-id="31c32-108">Scope</span></span>|<span data-ttu-id="31c32-109">次要</span><span class="sxs-lookup"><span data-stu-id="31c32-109">Minor</span></span>|
|<span data-ttu-id="31c32-110">版本</span><span class="sxs-lookup"><span data-stu-id="31c32-110">Version</span></span>|<span data-ttu-id="31c32-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="31c32-111">4.5.1</span></span>|
|<span data-ttu-id="31c32-112">类型</span><span class="sxs-lookup"><span data-stu-id="31c32-112">Type</span></span>|<span data-ttu-id="31c32-113">重定目标</span><span class="sxs-lookup"><span data-stu-id="31c32-113">Retargeting</span></span>|
|<span data-ttu-id="31c32-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="31c32-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
