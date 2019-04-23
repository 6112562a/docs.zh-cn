---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235148"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="54f9c-101">Sql_variant 数据使用 sql_variant 排序规则而不是数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="54f9c-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="54f9c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="54f9c-102">Details</span></span>|<span data-ttu-id="54f9c-103"><code>sql_variant</code> 数据使用 <code>sql_variant</code> 排序规则而不是数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="54f9c-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="54f9c-104">建议</span><span class="sxs-lookup"><span data-stu-id="54f9c-104">Suggestion</span></span>|<span data-ttu-id="54f9c-105">如果数据库排序规则与 <code>sql_variant</code> 排序规则不同，则此更改将解决可能的数据损坏。</span><span class="sxs-lookup"><span data-stu-id="54f9c-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="54f9c-106">依赖损坏的数据的应用程序可能会失败。</span><span class="sxs-lookup"><span data-stu-id="54f9c-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="54f9c-107">范围</span><span class="sxs-lookup"><span data-stu-id="54f9c-107">Scope</span></span>|<span data-ttu-id="54f9c-108">透明</span><span class="sxs-lookup"><span data-stu-id="54f9c-108">Transparent</span></span>|
|<span data-ttu-id="54f9c-109">Version</span><span class="sxs-lookup"><span data-stu-id="54f9c-109">Version</span></span>|<span data-ttu-id="54f9c-110">4.5</span><span class="sxs-lookup"><span data-stu-id="54f9c-110">4.5</span></span>|
|<span data-ttu-id="54f9c-111">类型</span><span class="sxs-lookup"><span data-stu-id="54f9c-111">Type</span></span>|<span data-ttu-id="54f9c-112">运行时</span><span class="sxs-lookup"><span data-stu-id="54f9c-112">Runtime</span></span>|
