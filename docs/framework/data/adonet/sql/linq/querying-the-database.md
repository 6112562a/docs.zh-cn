---
title: 查询数据库
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: 3c48879d8e3ae699ef749fc14923358174010aae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782069"
---
# <a name="querying-the-database"></a><span data-ttu-id="0fda1-102">查询数据库</span><span class="sxs-lookup"><span data-stu-id="0fda1-102">Querying the Database</span></span>
<span data-ttu-id="0fda1-103">本组主题说明如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 项目中开发和执行查询。</span><span class="sxs-lookup"><span data-stu-id="0fda1-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fda1-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="0fda1-104">In This Section</span></span>  
 [<span data-ttu-id="0fda1-105">如何：查询信息</span><span class="sxs-lookup"><span data-stu-id="0fda1-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="0fda1-106">简要说明为何 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询大体上与 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查询基本相同。</span><span class="sxs-lookup"><span data-stu-id="0fda1-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="0fda1-107">如何：以只读方式检索信息</span><span class="sxs-lookup"><span data-stu-id="0fda1-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="0fda1-108">说明在不打算更改数据时如何提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="0fda1-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="0fda1-109">如何：控制检索的相关数据量</span><span class="sxs-lookup"><span data-stu-id="0fda1-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="0fda1-110">说明如何控制与主目标一起检索的相关数据。</span><span class="sxs-lookup"><span data-stu-id="0fda1-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="0fda1-111">如何：筛选相关数据</span><span class="sxs-lookup"><span data-stu-id="0fda1-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="0fda1-112">说明如何通过使用子查询检索相关数据。</span><span class="sxs-lookup"><span data-stu-id="0fda1-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="0fda1-113">如何：关闭延迟加载</span><span class="sxs-lookup"><span data-stu-id="0fda1-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="0fda1-114">说明如何关闭延迟加载。</span><span class="sxs-lookup"><span data-stu-id="0fda1-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="0fda1-115">如何：直接执行 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="0fda1-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="0fda1-116">说明如何使用 SQL 语言提交查询。</span><span class="sxs-lookup"><span data-stu-id="0fda1-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="0fda1-117">如何：存储和重复使用查询</span><span class="sxs-lookup"><span data-stu-id="0fda1-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="0fda1-118">说明如何编译查询一次，但将其与不同的参数一起使用多次。</span><span class="sxs-lookup"><span data-stu-id="0fda1-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="0fda1-119">如何：处理查询中的复合键</span><span class="sxs-lookup"><span data-stu-id="0fda1-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="0fda1-120">说明如何在运算符只带一个自变量的情况下在查询中包含多列。</span><span class="sxs-lookup"><span data-stu-id="0fda1-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="0fda1-121">如何：同时检索多个对象</span><span class="sxs-lookup"><span data-stu-id="0fda1-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="0fda1-122">描述如何使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>。</span><span class="sxs-lookup"><span data-stu-id="0fda1-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0fda1-123">如何：在 DataContext 级别进行筛选</span><span class="sxs-lookup"><span data-stu-id="0fda1-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="0fda1-124">介绍 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 的另一用法。</span><span class="sxs-lookup"><span data-stu-id="0fda1-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0fda1-125">查询示例</span><span class="sxs-lookup"><span data-stu-id="0fda1-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="0fda1-126">提供许多查询示例。</span><span class="sxs-lookup"><span data-stu-id="0fda1-126">Provides many examples of queries.</span></span>
