---
title: 接口属性 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: af80f403942f59d672854c80830e175ef7ebaff5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652174"
---
# <a name="interface-properties-c-programming-guide"></a>接口属性（C# 编程指南）
可以在[接口](../../../csharp/language-reference/keywords/interface.md)上声明属性。 下面是接口属性访问器的示例：  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 接口属性的访问器没有正文。 因此，访问器的用途是指示属性为读写、只读还是只写。  
  
## <a name="example"></a>示例  
 在此示例中，接口 `IEmployee` 具有读写属性 `Name` 和只读属性 `Counter`。 类 `Employee` 实现 `IEmployee` 接口，并使用这两个属性。 程序读取新员工的姓名以及当前员工数，并显示员工名称和计算的员工数。  
  
 可以使用属性的完全限定名称，它引用其中声明成员的接口。 例如:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 这称为[显式接口实现](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)。 例如，如果 `Employee` 类正在实现接口 `ICitizen` 和接口 `IEmployee`，而这两个接口都具有 `Name` 属性，则需要用到显式接口成员实现。 即是说下列属性声明：  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 在 `IEmployee` 接口中实现 `Name` 属性，而以下声明：  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 在 `ICitizen` 接口中实现 `Name` 属性。  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>示例输出  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [属性](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [使用属性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [属性与索引器之间的比较](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)
- [索引器](../../../csharp/programming-guide/indexers/index.md)
- [接口](../../../csharp/programming-guide/interfaces/index.md)
