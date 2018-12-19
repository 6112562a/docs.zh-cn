---
title: '!= 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237813"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9d4fa-102">!= 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="9d4fa-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="9d4fa-103">如果操作数相等，不相等运算符 (`!=`) 返回 false，否则返回 true。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="9d4fa-104">不相等运算符针对 string 和 object 等所有类型进行预定义。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="9d4fa-105">用户定义的类型可以重载 `!=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d4fa-106">备注</span><span class="sxs-lookup"><span data-stu-id="9d4fa-106">Remarks</span></span>  
 <span data-ttu-id="9d4fa-107">对于预定义的值类型，如果其操作数的值不同，不相等运算符 (`!=`) 返回 true，否则返回 false。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="9d4fa-108">对于除 `string` 外的引用类型，如果两个操作数引用不同对象，`!=` 返回 true。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="9d4fa-109">对于 `string` 类型，`!=` 会比较字符串的值。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="9d4fa-110">用户定义的值类型可以重载 `!=` 运算符（请参阅[运算符](../../../csharp/language-reference/keywords/operator.md)）。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9d4fa-111">用户定义的引用类型情况也相似，但是默认情况下，`!=` 的行为如上述预定义和用户定义的引用类型所述。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="9d4fa-112">如果已重载 `!=`，则必须同时重载 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="9d4fa-113">对整数类型的操作通常可用于枚举。</span><span class="sxs-lookup"><span data-stu-id="9d4fa-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d4fa-114">示例</span><span class="sxs-lookup"><span data-stu-id="9d4fa-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9d4fa-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="9d4fa-115">See Also</span></span>

- [<span data-ttu-id="9d4fa-116">C# 参考</span><span class="sxs-lookup"><span data-stu-id="9d4fa-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9d4fa-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9d4fa-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9d4fa-118">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="9d4fa-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
