---
title: . 运算符 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: f5048761973e10bec9650469383e2f52cee74da4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235041"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2d5b0-103">.</span><span class="sxs-lookup"><span data-stu-id="2d5b0-103">.</span></span> <span data-ttu-id="2d5b0-104">运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2d5b0-104">Operator (C# Reference)</span></span>
<span data-ttu-id="2d5b0-105">点运算符 (`.`) 用于成员访问。</span><span class="sxs-lookup"><span data-stu-id="2d5b0-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="2d5b0-106">点运算符指定类型或命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="2d5b0-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="2d5b0-107">例如，点运算符用于访问 .NET Framework 类库中的特定方法：</span><span class="sxs-lookup"><span data-stu-id="2d5b0-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="2d5b0-108">例如，请考虑以下类：</span><span class="sxs-lookup"><span data-stu-id="2d5b0-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="2d5b0-109">变量 `s` 具有两个成员（`a` 和 `b`）；若要对其进行访问，请使用点运算符：</span><span class="sxs-lookup"><span data-stu-id="2d5b0-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="2d5b0-110">点还用于构成限定名称，即为指定它们所属的命名空间或接口等的名称。</span><span class="sxs-lookup"><span data-stu-id="2d5b0-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="2d5b0-111">using 指令使某些名称限定变成可选：</span><span class="sxs-lookup"><span data-stu-id="2d5b0-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="2d5b0-112">但如果标识符不明确，则必须对其进行限定：</span><span class="sxs-lookup"><span data-stu-id="2d5b0-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2d5b0-113">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2d5b0-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d5b0-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="2d5b0-114">See Also</span></span>

- [<span data-ttu-id="2d5b0-115">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2d5b0-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2d5b0-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2d5b0-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2d5b0-117">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="2d5b0-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
