---
title: 对 join 子句的结果进行排序（C# 中的 LINQ）
description: 了解如何对 C# 中的 LINQ join 子句的结果进行排序。
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659860"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="2d0b6-103">对 join 子句的结果进行排序</span><span class="sxs-lookup"><span data-stu-id="2d0b6-103">Order the results of a join clause</span></span>

<span data-ttu-id="2d0b6-104">此示例演示如何对联接运算的结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="2d0b6-105">请注意，排序在联接之后执行。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="2d0b6-106">虽然可以在联接之前将 `orderby` 子句用于一个或多个源序列，不过通常不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="2d0b6-107">某些 LINQ 提供程序可能不会在联接之后保留该排序。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="2d0b6-108">示例</span><span class="sxs-lookup"><span data-stu-id="2d0b6-108">Example</span></span>

<span data-ttu-id="2d0b6-109">此查询创建一个分组联接，然后基于类别元素（仍处于范围中）对组进行排序。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="2d0b6-110">在匿名类型初始值设定项内，一个子查询对来自产品序列的所有匹配元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="2d0b6-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d0b6-111">See also</span></span>

- [<span data-ttu-id="2d0b6-112">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2d0b6-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="2d0b6-113">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="2d0b6-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="2d0b6-114">join 子句</span><span class="sxs-lookup"><span data-stu-id="2d0b6-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
