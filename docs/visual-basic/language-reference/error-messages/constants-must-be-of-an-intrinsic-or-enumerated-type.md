---
title: 常量必须是内部类型或者枚举类型，不能是类、结构、类型参数或数组类型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: f82a548c820aec7d2ae13c30a67d778fc167a8b6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813101"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="6ca75-102">常量必须是内部类型或者枚举类型，不能是类、结构、类型参数或数组类型</span><span class="sxs-lookup"><span data-stu-id="6ca75-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="6ca75-103">已尝试声明为类、 结构或数组类型，或由包含泛型类型定义的类型参数的常量。</span><span class="sxs-lookup"><span data-stu-id="6ca75-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="6ca75-104">常量必须是内部类型 (`Boolean`， `Byte`， `Date`， `Decimal`， `Double`， `Integer`， `Long`， `Object`， `SByte`， `Short`， `Single`， `String`， `UInteger`， `ULong`，或`UShort`)，或`Enum`类型基于整型类型之一。</span><span class="sxs-lookup"><span data-stu-id="6ca75-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="6ca75-105">**错误 ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="6ca75-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ca75-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="6ca75-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6ca75-107">声明常量用作内部函数或`Enum`类型。</span><span class="sxs-lookup"><span data-stu-id="6ca75-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="6ca75-108">一个常数，也可以是特殊值，如`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="6ca75-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="6ca75-109">编译器会考虑这些预定义的值为相应的内部类型。</span><span class="sxs-lookup"><span data-stu-id="6ca75-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca75-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ca75-110">See also</span></span>

- [<span data-ttu-id="6ca75-111">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="6ca75-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="6ca75-112">数据类型</span><span class="sxs-lookup"><span data-stu-id="6ca75-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6ca75-113">数据类型</span><span class="sxs-lookup"><span data-stu-id="6ca75-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
