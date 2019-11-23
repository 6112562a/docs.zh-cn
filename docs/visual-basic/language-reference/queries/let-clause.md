---
title: Let 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350438"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="b0495-102">Let 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0495-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="b0495-103">Computes a value and assigns it to a new variable within the query.</span><span class="sxs-lookup"><span data-stu-id="b0495-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0495-104">语法</span><span class="sxs-lookup"><span data-stu-id="b0495-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="b0495-105">部件</span><span class="sxs-lookup"><span data-stu-id="b0495-105">Parts</span></span>  
  
|<span data-ttu-id="b0495-106">术语</span><span class="sxs-lookup"><span data-stu-id="b0495-106">Term</span></span>|<span data-ttu-id="b0495-107">定义</span><span class="sxs-lookup"><span data-stu-id="b0495-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="b0495-108">必须的。</span><span class="sxs-lookup"><span data-stu-id="b0495-108">Required.</span></span> <span data-ttu-id="b0495-109">An alias that can be used to reference the results of the supplied expression.</span><span class="sxs-lookup"><span data-stu-id="b0495-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="b0495-110">必须的。</span><span class="sxs-lookup"><span data-stu-id="b0495-110">Required.</span></span> <span data-ttu-id="b0495-111">An expression that will be evaluated and assigned to the specified variable.</span><span class="sxs-lookup"><span data-stu-id="b0495-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0495-112">备注</span><span class="sxs-lookup"><span data-stu-id="b0495-112">Remarks</span></span>  
 <span data-ttu-id="b0495-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span><span class="sxs-lookup"><span data-stu-id="b0495-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="b0495-114">The alias can be used in other clauses, such as the `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="b0495-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="b0495-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span><span class="sxs-lookup"><span data-stu-id="b0495-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="b0495-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span><span class="sxs-lookup"><span data-stu-id="b0495-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="b0495-117">Separate each assignment with a comma (,).</span><span class="sxs-lookup"><span data-stu-id="b0495-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0495-118">示例</span><span class="sxs-lookup"><span data-stu-id="b0495-118">Example</span></span>  
 <span data-ttu-id="b0495-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span><span class="sxs-lookup"><span data-stu-id="b0495-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="b0495-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0495-120">See also</span></span>

- [<span data-ttu-id="b0495-121">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="b0495-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b0495-122">查询</span><span class="sxs-lookup"><span data-stu-id="b0495-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b0495-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="b0495-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b0495-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="b0495-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b0495-125">Where 子句</span><span class="sxs-lookup"><span data-stu-id="b0495-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
