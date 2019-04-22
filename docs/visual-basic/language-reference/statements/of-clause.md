---
title: Of 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823436"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="7a367-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a367-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="7a367-103">引入了`Of`子句，用于标识*的类型形参*上*泛型*类、 结构、 接口、 委托或过程。</span><span class="sxs-lookup"><span data-stu-id="7a367-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="7a367-104">有关泛型类型的信息，请参阅[在 Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7a367-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="7a367-105">使用的关键字</span><span class="sxs-lookup"><span data-stu-id="7a367-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="7a367-106">下面的代码示例使用`Of`关键字来定义采用两个类型参数的类的轮廓。</span><span class="sxs-lookup"><span data-stu-id="7a367-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="7a367-107">它*约束，使之*`keyType`参数<xref:System.IComparable>接口，这意味着使用的代码必须提供实现一个类型实参<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="7a367-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="7a367-108">这是必需的以便`add`过程可以调用<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="7a367-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a367-109">有关约束的详细信息，请参阅 [Type List](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="7a367-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="7a367-110">如果您完成前面的类定义，可以构造各种`dictionary`从它的类。</span><span class="sxs-lookup"><span data-stu-id="7a367-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="7a367-111">提供给类型`entryType`和`keyType`确定哪种类型的条目类保存并与每个条目关联哪种类型的密钥。</span><span class="sxs-lookup"><span data-stu-id="7a367-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="7a367-112">由于该约束，必须提供给`keyType`实现的类型<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="7a367-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="7a367-113">下面的代码示例创建一个对象，保存`String`条目并将关联`Integer`其中每个密钥。</span><span class="sxs-lookup"><span data-stu-id="7a367-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="7a367-114">`Integer` 实现<xref:System.IComparable>，因此在满足约束`keyType`。</span><span class="sxs-lookup"><span data-stu-id="7a367-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="7a367-115">`Of` 关键字可用于以下上下文中：</span><span class="sxs-lookup"><span data-stu-id="7a367-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7a367-116">Class 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="7a367-117">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="7a367-118">Function 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="7a367-119">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="7a367-120">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="7a367-121">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="7a367-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a367-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a367-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="7a367-123">类型列表</span><span class="sxs-lookup"><span data-stu-id="7a367-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="7a367-124">Visual Basic 中的泛型类型</span><span class="sxs-lookup"><span data-stu-id="7a367-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7a367-125">In</span><span class="sxs-lookup"><span data-stu-id="7a367-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="7a367-126">Out</span><span class="sxs-lookup"><span data-stu-id="7a367-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
