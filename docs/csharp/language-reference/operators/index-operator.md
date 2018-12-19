---
title: '[] 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 3e2ce5c4b74cbf79e00410791ffcc31368f78648
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243993"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6bdaf-102">[] 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="6bdaf-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="6bdaf-103">方括号 (`[]`) 可用于数组、索引器和属性。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="6bdaf-104">还可用于指针。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bdaf-105">备注</span><span class="sxs-lookup"><span data-stu-id="6bdaf-105">Remarks</span></span>  
 <span data-ttu-id="6bdaf-106">数组类型是后接 `[]` 的类型：</span><span class="sxs-lookup"><span data-stu-id="6bdaf-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="6bdaf-107">若要访问数组的元素，请使用方括号将所需元素的索引括起来：</span><span class="sxs-lookup"><span data-stu-id="6bdaf-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="6bdaf-108">如果数组索引超出范围，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="6bdaf-109">不能重载数组索引运算符；但类型可以定义采用一个或多个参数的索引器。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="6bdaf-110">索引器参数括在方括号内，这一点与数组索引类似，但可以将索引器参数声明为任何类型，这一点与数组索引不同，后者必须为整型。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="6bdaf-111">例如，.NET Framework 定义 `Hashtable` 类型，该类型将任意类型的键和值关联在一起：</span><span class="sxs-lookup"><span data-stu-id="6bdaf-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="6bdaf-112">方括号还用于指定[属性](../../../csharp/programming-guide/concepts/attributes/index.md)：</span><span class="sxs-lookup"><span data-stu-id="6bdaf-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="6bdaf-113">可以使用方括号来指定指针索引：</span><span class="sxs-lookup"><span data-stu-id="6bdaf-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="6bdaf-114">不执行边界检查。</span><span class="sxs-lookup"><span data-stu-id="6bdaf-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6bdaf-115">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="6bdaf-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6bdaf-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="6bdaf-116">See Also</span></span>

- [<span data-ttu-id="6bdaf-117">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6bdaf-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6bdaf-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6bdaf-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6bdaf-119">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="6bdaf-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="6bdaf-120">数组</span><span class="sxs-lookup"><span data-stu-id="6bdaf-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="6bdaf-121">索引器</span><span class="sxs-lookup"><span data-stu-id="6bdaf-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="6bdaf-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="6bdaf-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="6bdaf-123">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="6bdaf-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
