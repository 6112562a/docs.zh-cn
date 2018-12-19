---
title: 对象和集合初始值设定项 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 60c4e8c5b83ee1c279bf8e7f4905ef9f2cf814b4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243161"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>对象和集合初始值设定项（C# 编程指南）
使用对象初始值设定项，你可以在创建对象时向对象的任何可访问字段或属性分配值，而无需调用后跟赋值语句行的构造函数。 利用对象初始值设定项语法，你可为构造函数指定参数或忽略参数（以及括号语法）。  以下示例演示如何使用具有命名类型 `Cat` 的对象初始值设定项以及如何调用默认构造函数。 请注意，自动实现的属性在 `Cat` 类中的用法。 有关详细信息，请参阅[自动实现的属性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
对象初始值设定项语法允许你创建一个实例，然后将具有其分配属性的新建对象指定给赋值中的变量。
  
## <a name="object-initializers-with-anonymous-types"></a>具有匿名类型的对象初始值设定项  
 尽管对象初始值设定项可用于任何上下文中，但它们在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询表达式中特别有用。 查询表达式常使用只能通过使用对象初始值设定项进行初始化的[匿名类型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)，如下面的声明所示。  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 利用匿名类型，[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询表达式中的 `select` 子句可以将原始序列的对象转换为其值和形状可能不同于原始序列的对象。 如果你只想存储某个序列中每个对象的部分信息，则这很有用。 在下面的示例中，假定产品对象 (`p`) 包含很多字段和方法，而你只想创建包含产品名和单价的对象序列。  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 执行此查询时，`productInfos` 变量将包含一系列对象，这些对象可以在 `foreach` 语句中进行访问，如下面的示例所示：  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 新的匿名类型中的每个对象都具有两个公共属性，这两个属性接收与原始对象中的属性或字段相同的名称。 你还可在创建匿名类型时重命名字段；下面的示例将 `UnitPrice` 字段重命名为 `Price`。  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a>集合初始值设定项  
 在初始化实现 <xref:System.Collections.IEnumerable> 的集合类型和初始化使用适当的签名作为实例方法或扩展方法的 `Add` 时，集合初始值设定项允许指定一个或多个元素初始值设定项。 元素初始值设定项可以是简单的值、表达式或对象初始值设定项。 通过使用集合初始值设定项，你将无需在源代码中指定对该类的 `Add` 方法的多个调用；编译器将添加这些调用。  
  
 下面的示例演示了两个简单的集合初始值设定项：  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 下面的集合初始值设定项使用对象初始值设定项来初始化上一个示例中定义的 `Cat` 类的对象。 请注意，各个对象初始值设定项分别括在大括号中且用逗号隔开。  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 如果集合的 `Add` 方法允许，则可以将 [null](../../../csharp/language-reference/keywords/null.md) 指定为集合初始值设定项中的一个元素。  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 如果集合支持索引，可以指定索引元素。  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>示例

 下例结合了对象和集合初始值设定项的概念。

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 在下面的示例中，实现包含 `Add` 方法（具有多个参数）的 <xref:System.Collections.IEnumerable> 的对象允许在列表中每项具有多个元素的集合初始值设定项与 `Add` 方法的签名对应。 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add` 方法可使用 `params` 关键字来获取可变数量的自变量，如下例中所示。 此示例还演示了索引器的自定义实现，以及使用索引初始化集合。
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [LINQ 查询表达式](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [匿名类型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
