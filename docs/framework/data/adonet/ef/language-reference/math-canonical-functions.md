---
title: 数学规范函数
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760631"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="7de2a-102">数学规范函数</span><span class="sxs-lookup"><span data-stu-id="7de2a-102">Math Canonical Functions</span></span>

<span data-ttu-id="7de2a-103">实体 SQL 包括以下数学规范函数：</span><span class="sxs-lookup"><span data-stu-id="7de2a-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="7de2a-104">Abs(value)</span><span class="sxs-lookup"><span data-stu-id="7de2a-104">Abs(value)</span></span>

<span data-ttu-id="7de2a-105">返回 `value` 的绝对值。</span><span class="sxs-lookup"><span data-stu-id="7de2a-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="7de2a-106">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-106">**Arguments**</span></span>

<span data-ttu-id="7de2a-107">`Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7de2a-108">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-108">**Return Value**</span></span>

<span data-ttu-id="7de2a-109">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-109">The type of `value`.</span></span>

<span data-ttu-id="7de2a-110">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="7de2a-111">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="7de2a-111">Ceiling(value)</span></span>

<span data-ttu-id="7de2a-112">返回不小于 `value` 的最小整数。</span><span class="sxs-lookup"><span data-stu-id="7de2a-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="7de2a-113">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-113">**Arguments**</span></span>

<span data-ttu-id="7de2a-114">一个`Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7de2a-115">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-115">**Return Value**</span></span>

<span data-ttu-id="7de2a-116">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-116">The type of `value`.</span></span>

<span data-ttu-id="7de2a-117">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="7de2a-118">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="7de2a-118">Floor(value)</span></span>

<span data-ttu-id="7de2a-119">返回不大于 `value` 的最大整数。</span><span class="sxs-lookup"><span data-stu-id="7de2a-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="7de2a-120">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-120">**Arguments**</span></span>

<span data-ttu-id="7de2a-121">一个`Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7de2a-122">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-122">**Return Value**</span></span>

<span data-ttu-id="7de2a-123">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-123">The type of `value`.</span></span>

<span data-ttu-id="7de2a-124">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="7de2a-125">Power(值, 指数)</span><span class="sxs-lookup"><span data-stu-id="7de2a-125">Power(value, exponent)</span></span>

<span data-ttu-id="7de2a-126">返回对指定的 `value` 求指定的 `exponent` 幂次所得的结果。</span><span class="sxs-lookup"><span data-stu-id="7de2a-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="7de2a-127">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="7de2a-128">`Int32, Int64, Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="7de2a-129">`Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="7de2a-130">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-130">**Return Value**</span></span>

<span data-ttu-id="7de2a-131">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-131">The type of `value`.</span></span>

<span data-ttu-id="7de2a-132">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="7de2a-133">Round(value)</span><span class="sxs-lookup"><span data-stu-id="7de2a-133">Round(value)</span></span>

<span data-ttu-id="7de2a-134">返回 `value` 的整数部分，舍入到最近的整数。</span><span class="sxs-lookup"><span data-stu-id="7de2a-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="7de2a-135">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-135">**Arguments**</span></span>

<span data-ttu-id="7de2a-136">一个`Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7de2a-137">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-137">**Return Value**</span></span>

<span data-ttu-id="7de2a-138">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-138">The type of `value`.</span></span>

<span data-ttu-id="7de2a-139">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="7de2a-140">Round(值, 位数)</span><span class="sxs-lookup"><span data-stu-id="7de2a-140">Round(value, digits)</span></span>

<span data-ttu-id="7de2a-141">返回 `value`，舍入到最近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="7de2a-142">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="7de2a-143">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="7de2a-144">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="7de2a-145">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-145">**Return Value**</span></span>

<span data-ttu-id="7de2a-146">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-146">The type of `value`.</span></span>

<span data-ttu-id="7de2a-147">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="7de2a-148">Truncate(值, 位数)</span><span class="sxs-lookup"><span data-stu-id="7de2a-148">Truncate(value, digits)</span></span>

<span data-ttu-id="7de2a-149">返回 `value`，截断至最近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="7de2a-150">**参数**</span><span class="sxs-lookup"><span data-stu-id="7de2a-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="7de2a-151">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="7de2a-152">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="7de2a-153">**返回值**</span><span class="sxs-lookup"><span data-stu-id="7de2a-153">**Return Value**</span></span>

<span data-ttu-id="7de2a-154">`value` 的类型。</span><span class="sxs-lookup"><span data-stu-id="7de2a-154">The type of `value`.</span></span>

<span data-ttu-id="7de2a-155">**示例**</span><span class="sxs-lookup"><span data-stu-id="7de2a-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="7de2a-156">如果提供 `null` 输入，则这些函数返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="7de2a-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="7de2a-157">Microsoft SQL 客户端托管提供程序中提供了等效功能。</span><span class="sxs-lookup"><span data-stu-id="7de2a-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="7de2a-158">有关详细信息，请参阅[用于实体框架函数的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="7de2a-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de2a-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="7de2a-159">See also</span></span>

- [<span data-ttu-id="7de2a-160">规范函数</span><span class="sxs-lookup"><span data-stu-id="7de2a-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
