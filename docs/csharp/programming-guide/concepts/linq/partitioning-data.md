---
title: 数据分区 (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591588"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="94e01-102">数据分区 (C#)</span><span class="sxs-lookup"><span data-stu-id="94e01-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="94e01-103">LINQ 中的分区是指将输入序列划分为两个部分的操作，无需重新排列元素，然后返回其中一个部分。</span><span class="sxs-lookup"><span data-stu-id="94e01-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="94e01-104">下图显示对字符序列进行三种不同的分区操作的结果。</span><span class="sxs-lookup"><span data-stu-id="94e01-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="94e01-105">第一个操作返回序列中的前三个元素。</span><span class="sxs-lookup"><span data-stu-id="94e01-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="94e01-106">第二个操作跳过前三个元素，返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="94e01-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="94e01-107">第三个操作跳过序列中的前两个元素，返回接下来的三个元素。</span><span class="sxs-lookup"><span data-stu-id="94e01-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![显示三个 LINQ 分区操作的图示。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="94e01-109">下面一节列出了对序列进行分区的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="94e01-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="94e01-110">运算符</span><span class="sxs-lookup"><span data-stu-id="94e01-110">Operators</span></span>  
  
|<span data-ttu-id="94e01-111">运算符名称</span><span class="sxs-lookup"><span data-stu-id="94e01-111">Operator Name</span></span>|<span data-ttu-id="94e01-112">说明</span><span class="sxs-lookup"><span data-stu-id="94e01-112">Description</span></span>|<span data-ttu-id="94e01-113">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="94e01-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="94e01-114">详细信息</span><span class="sxs-lookup"><span data-stu-id="94e01-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="94e01-115">Skip</span><span class="sxs-lookup"><span data-stu-id="94e01-115">Skip</span></span>|<span data-ttu-id="94e01-116">跳过序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="94e01-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="94e01-117">不适用。</span><span class="sxs-lookup"><span data-stu-id="94e01-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="94e01-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="94e01-118">SkipWhile</span></span>|<span data-ttu-id="94e01-119">基于谓词函数跳过元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="94e01-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="94e01-120">不适用。</span><span class="sxs-lookup"><span data-stu-id="94e01-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="94e01-121">Take</span><span class="sxs-lookup"><span data-stu-id="94e01-121">Take</span></span>|<span data-ttu-id="94e01-122">获取序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="94e01-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="94e01-123">不适用。</span><span class="sxs-lookup"><span data-stu-id="94e01-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="94e01-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="94e01-124">TakeWhile</span></span>|<span data-ttu-id="94e01-125">基于谓词函数获取元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="94e01-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="94e01-126">不适用。</span><span class="sxs-lookup"><span data-stu-id="94e01-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="94e01-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94e01-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="94e01-128">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="94e01-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
