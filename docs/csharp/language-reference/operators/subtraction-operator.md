---
title: '- 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633001"
---
# <a name="--operator-c-reference"></a>- 运算符（C# 参考）

`-` 运算符既可作为一元运算符也可作为二元运算符。

## <a name="remarks"></a>备注

为所有数值类型预定义了一元 `-` 运算符。 对数值类型进行一元 `-` 运算的结果是操作数的数值求反运算。

针对所有数值和枚举类型预定义二元 `-` 运算符，从第一个操作数中减去第一个操作数。

委托类型也提供二元 `-` 运算符，该运算符执行委托移除。

用户定义的类型可重载一元 `-` 运算符和二元 `-` 运算符。 有关详细信息，请参阅[运算符关键字](../keywords/operator.md)。

## <a name="example"></a>示例

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 运算符](index.md)
