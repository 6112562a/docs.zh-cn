---
title: C# 6 中的新增功能 - C# 指南
description: 了解 C# 版本 6 中的新增功能
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: ad3515e1fc7d70e1377f007276c369d2884780f0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194028"
---
# <a name="whats-new-in-c-6"></a>C# 6 中的新增功能

C# 6.0 版本包含许多可提高开发人员工作效率的功能。 此版本中的功能包括：

* [只读自动属性](#read-only-auto-properties)：
    - 可以创建只能在构造函数中设置的只读自动属性。
* [自动属性初始化表达式](#auto-property-initializers)：
    - 可以编写初始化表达式来设置自动属性的初始值。
* [Expression-bodied 函数成员](#expression-bodied-function-members)：
    - 可以使用 lambda 表达式创建单行方法。
* [using static](#using-static)：
    - 可以将单个类的所有方法导入当前命名空间。
* [NULL 条件运算符](#null-conditional-operators)：
    - 可以简洁、安全地访问对象的成员，同时仍能使用 null 条件运算符检查 null。
* [字符串内插](#string-interpolation)：
    - 可以使用内联表达式（而不是位置参数）编写字符串格式设置表达式。
* [异常筛选器](#exception-filters)：
    - 可以基于异常或其他程序状态的属性捕获表达式。 
* [`nameof` 表达式](#the-nameof-expression)：
    - 可以让编译器生成符号的字符串表示形式。
* [Catch 和 Finally 块中的 Await](#await-in-catch-and-finally-blocks)：
    - 可以在先前不允许使用 `await` 表达式的位置使用它们。
* [索引初始化表达式](#index-initializers)：
    - 可以为关联容器及序列容器创建初始化表达式。
* [集合初始值设定项的扩展方法](#extension-add-methods-in-collection-initializers)：
    - 除成员方法以外，集合初始值设定项还可以依赖可访问的扩展方法。
* [改进了重载解析](#improved-overload-resolution)：
    - 先前生成了不明确的方法调用的某些构造现在可以正确解析。
* [`deterministic` 编译器选项](#deterministic-compiler-output)：
    - 该确定性的编译器选项确保同一源的后续编译生成同样的二进制输出内容。

这些功能的总体效果是让你编写的代码更简洁、更具可读性。 该语法不像许多常见做法那样繁琐。 可以更轻松地看出设计意图。 好好了解这些功能有助于你提高工作效率、编写更具可读性的代码，并更专注于核心功能而不是语言的构造。

此主题的其余部分提供有关上述每种功能的详细信息。

## <a name="auto-property-enhancements"></a>自动属性增强功能

通过自动实现属性的语法（通常称为“自动属性”），可轻松创建具有简单 get 和 set 访问器的属性：

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

但是，这种简单的语法限制了你可以使用自动属性支持的设计类型。 C# 6 改进了自动属性功能，以便用户可以在更多方案中使用它们。 无需频繁地求助于手动声明和操纵支持字段的更详细的语法。

新语法可处理适用于只读属性的方案以及初始化自动属性后的变量存储的方案。

### <a name="read-only-auto-properties"></a>只读自动属性

只读自动属性提供了更简洁的语法来创建不可变类型。 在 C# 的早期版本中，创建不可变类型的最直接方法是声明专用资源库：

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
使用此语法，编译器并不能确保类型是不可变的。 它仅强制规定不会从类外部的任何代码修改 `FirstName` 和 `LastName` 属性。

只读自动属性实现真正的只读行为。 你声明仅具有 get 访问器的自动属性：

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` 和 `LastName` 属性只能在构造函数的主体中设置：

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

尝试在另一种方法中设置 `LastName` 会生成 `CS0200` 编译错误：

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

此功能实现用于创建不可变类型和使用更简洁且方便的自动属性语法的真正语言支持。

如果添加此语法不会删除可访问的方法，则为[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。

### <a name="auto-property-initializers"></a>自动属性初始化表达式

自动属性初始值设定项可让你在属性声明中声明自动属性的初始值。  在早期版本中，这些属性需要具有资源库，你需要使用该资源库来初始化支持字段使用的数据存储。 对于包含姓名和学生成绩列表的学生，请考虑此类：

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
随着此类的增长，你可以包含其他构造函数。 每个构造函数都需要初始化此字段，否则将引入错误。

通过 C# 6，可为自动属性声明中的自动属性所使用的存储分配初始值：

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` 成员在声明它的位置处被初始化。 这样，就能更容易地仅执行一次初始化。 初始化是属性声明的一部分，可更轻松地将存储分配等同于 `Student` 对象的公用接口。

属性初始化表达式可与读/写属性以及只读属性一起使用，如下所示。

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Expression-bodied 函数成员

我们编写的很多成员的主体只包含一条可以表示为表达式的语句。 可通过改为编写 expression-bodied 成员来简化该语法。 这适用于方法和只读属性。 例如，重写 `ToString()` 通常是理想之选：

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

还可以在只读属性中使用 expression-bodied 成员：

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

将现有成员更改为 expression bodied 成员是[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。


## <a name="using-static"></a>using static

using static 增强功能可用于导入单个类的静态方法。 以前，`using` 语句将所有类型导入命名空间中。 

通常，我们在整个代码中使用类的静态方法。 重复键入类名可能会导致代码的含义难以理解。 一个常见的例子是当你编写执行许多数值计算的类时。
你的代码中将充满 <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A> 以及对 <xref:System.Math> 类中不同方法的其他调用。 新的 `using static` 语法可以使这些类更简洁、更易读。 指定要使用的类：

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

现在，可以使用 <xref:System.Math> 类中的任何静态方法而不必限定 <xref:System.Math> 类。 <xref:System.Math> 类是此功能的一个很好的用例，因为它不包含任何实例方法。 还可以使用 `using static` 为具有静态和实例方法的类导入类的静态方法。 最有用的示例之一是 <xref:System.String>：

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> 在 static using 语句中必须使用完全限定的类名 `System.String`。 而不能使用 `string` 关键字。 

现在可以调用 <xref:System.String> 类中定义的静态方法，而不必将这些方法限定为该类的成员：

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` 功能和扩展方法以有趣的方式进行交互，并且该语言设计包含一些特定处理这些交互的规则。 目标是尽可能减少现有基本代码（包括你的基本代码）中发生重大更改的可能性。

仅在使用扩展方法调用语法调用扩展方法（而不是作为静态方法调用）时，扩展方法才在范围内。
你在 LINQ 查询中会经常看到这种情况。 可以通过导入 <xref:System.Linq.Enumerable> 来导入 LINQ 模式。

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

这将导入 <xref:System.Linq.Enumerable> 类中的所有方法。
但是，扩展方法仅在作为扩展方法调用时才在范围内。 如果使用静态方法语法调用扩展方法，则它们不在范围内：

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

这个决定是因为扩展方法通常使用扩展方法调用表达式来调用。 在使用静态方法调用语法调用它们的罕见情况下，是为了解析多义性。
在调用中要求使用类名似乎是比较明智的做法。

`static using` 还有最后一项功能。 `static using` 指令还可以导入任何嵌套的类型。 这样，你可以引用任何嵌套的类型，而无需限定。

## <a name="null-conditional-operators"></a>Null 条件运算符

Null 值使代码变得复杂。 需要检查变量的每个访问，以确保没有取消对 `null` 的引用。 Null 条件运算符使这些检查更轻松、更流畅。

只需将成员访问 `.` 替换为 `?.`：

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

在前面的示例中，如果 Person 对象是 `null`，则将变量 `first` 赋值为 `null`。 否则，它将被分配 `FirstName` 属性的值。 最重要的是，`?.` 意味着当 `person` 变量为 `null` 时，此行代码不会生成 `NullReferenceException`。 它会短路并生成 `null`。

此外，请注意，无论 `person` 的值是什么，此表达式均返回 `string`。
在短路的情况下，键入返回的 `null` 值以匹配整个表达式。

通常，可以将此构造与 null 合并运算符一起使用，以在其中一个属性为 `null` 时分配默认值：

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

`?.` 运算符的右侧操作数不仅限于属性或字段。
还可以将其用于有条件地调用方法。 具有 null 条件运算符的成员函数的最常见用法是用于安全地调用可能为 `null` 的委托（或事件处理程序）。  方法是使用 `?.` 运算符调用该委托的 `Invoke` 方法来访问成员。 可以在  
[委托模式](../delegates-patterns.md#handling-null-delegates)主题中看到一个示例。

`?.` 运算符的规则确保运算符的左侧仅计算一次。 这很重要，它可实现许多语法，包括使用事件处理程序的示例。 让我们从事件处理程序的使用开始。 在以前的 C# 版本中，建议编写与下面类似的代码：

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

它的推荐度高于以下较简单的语法：

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> 前一个示例引入了一个争用条件。 在针对 `null` 进行检查时，`SomethingHappened` 事件可能具有订阅服务器，在引发该事件之前这些订阅服务器可能已被删除。 这会导致引发 <xref:System.NullReferenceException>。

在第二个版本中，`SomethingHappened` 事件处理程序在测试时可能为非 null，但如果其他代码删除处理程序，则在调用事件处理程序时，它可能仍为 null。

编译器生成 `?.` 运算符的代码，以确保 `?.` 表达式的左侧 (`this.SomethingHappened`) 计算一次，并且缓存结果：

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

通过确保左侧仅计算一次，可在 `?.` 的左侧使用任何表达式（包括方法调用）。即使它们具有副作用，但因为只计算一次，所以副作用只产生一次 。 可以在有关[事件](../events-overview.md#language-support-for-events)的内容中看到一个示例。

## <a name="string-interpolation"></a>字符串内插

C# 6 包含新语法，用于从字符串和嵌入的表达式编写字符串，可以通过计算这些字符串来生成其他字符串值。

传统上，需要在类似 <xref:System.String.Format%2A?displayProperty=nameWithType> 的方法中使用位置参数：

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

使用 C# 6，新的[字符串内插](../language-reference/tokens/interpolated.md)功能可以在字符串中嵌入表达式。 只需在字符串前面加上 `$`：

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

本示例使用替代表达式的属性表达式。 可以扩展此语法以使用任何表达式。 例如，可以在内插过程中计算学生的成绩平均值：

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

运行前面的示例，你会发现 `Grades.Average()` 的输出的小数位数可能比你需要的多。 字符串内插语法支持可使用前面的格式设置方法的所有格式字符串。 在大括号内指定格式字符串。 在要设置格式的表达式后面添加 `:`：

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

上一行代码将 `Grades.Average()` 的值格式设置为具有两位小数的浮点数。

`:` 始终解释为要设置格式的表达式和格式字符串之间的分隔符。 当表达式以另一种方式（如[条件运算符](../language-reference/operators/conditional-operator.md)）使用 `:` 时，这可能会产生问题：

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

在上一示例中，`:` 解析为格式字符串的开头，而不是条件运算符的一部分。 在发生此问题的所有情况下，可以用括号将表达式括起来，强制编译器按照你的意图解释该表达式：

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

对可以放在大括号之间的表达式没有任何限制。 可以在内插字符串中执行复杂的 LINQ 查询，以执行计算并显示结果：

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

可以从此示例中看出，甚至可以将字符串内插表达式嵌套在另一个字符串内插表达式中。 此示例在生产代码中很有可能比你想的更加复杂。
但它说明了该功能的范围。 任何 C# 表达式都可以放置在内插字符串的大括号之间。

若要开始使用字符串内插，请阅读 [C# 中的字符串内插](../tutorials/intro-to-csharp/interpolated-strings.yml)交互式教程。

### <a name="string-interpolation-and-specific-cultures"></a>字符串内插和特定区域性

前面部分中显示的所有示例使用执行代码的计算机上的当前区域性设置字符串格式。 通常，可能需要使用特定区域性设置生成的字符串的格式。
为此，请利用通过字符串内插生成的对象可以隐式转换为 <xref:System.FormattableString?displayProperty=nameWithType> 这一事实。

<xref:System.FormattableString> 实例包含组合格式字符串，以及在将其转换为字符串之前评估表达式的结果。 在设置字符串的格式时，可以使用 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法指定区域性。 例如，以下示例使用德国区域性生成字符串。 （它使用“,”字符作为小数分隔符，使用“.”字符作为千位分隔符。）

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

有关详细信息，请参阅[字符串内插](../language-reference/tokens/interpolated.md)一文和 [C# 中的字符串内插](../tutorials/string-interpolation.md)教程。

## <a name="exception-filters"></a>异常筛选器

C# 6 中的另一个新功能是异常筛选器。 异常筛选器是确定何时应该应用给定的 catch 子句的子句。
如果用于异常筛选器的表达式计算结果为 `true`，则 catch 子句将对异常执行正常处理。 如果表达式计算结果为 `false`，则将跳过 `catch` 子句。

一种用途是检查有关异常的信息，以确定 `catch` 子句是否可以处理该异常：

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

由异常筛选器生成的代码提供了有关已引发且未处理的异常的更好信息。 在将异常筛选器添加到语言之前，需要创建如下所示的代码：

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

这两个示例中，引发异常的点发生了更改。
在前一个代码中，使用了 `throw` 子句，对故障转储的任何堆栈跟踪分析或检查都将显示异常是从 catch 子句中的 `throw` 语句引发的。 实际的异常对象将包含原始调用堆栈，但是在此引发点与原始引发点位置之间的调用堆栈中的任何变量的所有其他信息已丢失。 

对比使用异常筛选器的代码的处理方式：异常筛选器表达式的计算结果为 `false`。 因此，执行决不会进入 `catch` 子句。 因为 `catch` 子句不会执行，不会发生堆栈展开。 这表示将保留原始引发位置，以用于以后将会发生的任何调试活动。

每当需要评估异常的字段或属性，而不是仅仅依赖异常类型时，请使用异常筛选器保留更多调试信息。

使用异常筛选器的另一种推荐模式是将其用于日志记录例程。 这种用法还会利用当异常筛选器计算结果为 `false` 时，保留异常引发点的方式。

日志记录方法将是这样一种方法：其参数为无条件返回 `false` 的异常：

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

每当要记录异常时，可以添加一个 catch 子句，并将此方法用作异常筛选器：

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

永远不会捕获异常，因为 `LogException` 方法始终返回 `false`。 始终为 false 的异常筛选器意味着可以将此日志记录处理程序放置在任何其他异常处理程序之前：

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

前一示例中强调了异常筛选器的一个非常重要的方面。
通过异常筛选器，可实现以下方案：较常规的异常 catch 子句可出现在较具体的 catch 子句前。 也可以在多个 catch 子句中出现相同的异常类型：

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

另一种建议模式有助于防止 catch 子句在附加调试器时处理异常。 通过此技术，可以使用调试器运行应用程序，并在引发异常时停止执行。

在代码中添加一个异常筛选器，使任何恢复代码仅在未附加调试器时执行：

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

在代码中添加之后，将调试器设置为在所有未处理的异常处中断。 在调试器下运行程序，每当 `PerformFailingOperation()` 引发 `RecoverableException` 时，调试器就会中断。
调试器将中断程序，因为不会执行 catch 子句（由于异常筛选器返回 false）。

## <a name="the-nameof-expression"></a>`nameof` 表达式

`nameof` 表达式的计算结果为符号的名称。 每当需要变量、属性或成员字段的名称时，这是让工具正常运行的好办法。

`nameof` 的其中一个最常见的用途是提供引起异常的符号的名称：

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

另一个用途是用于实现 `INotifyPropertyChanged` 接口的基于 XAML 的应用程序：

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

相较于使用常量字符串，使用 `nameof` 运算符的优点是工具可以了解符号。 如果使用重构工具重命名符号，会在 `nameof` 表达式中对其重命名。 常量字符串没有这一优势。 请在你最喜爱的编辑器中亲自尝试一下：重命名一个变量，任何 `nameof` 表达式也将更新。

`nameof` 表达式生成其参数（在前面的示例中为 `LastName`）的非限定名称，即使使用参数的完全限定名称也是如此：

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

此 `nameof` 表达式生成 `FirstName`，而不是 `UXComponents.ViewModel.FirstName`。

## <a name="await-in-catch-and-finally-blocks"></a>Catch 和 Finally 块中的 Await

C# 5 对于可放置 `await` 表达式的位置有若干限制。
其中一个限制已在 C# 6 中删除。 现在，可以在 `catch` 或 `finally` 表达式中使用 `await`。 

在 catch 和 finally 块中添加 await 表达式可能会使这些表达式的处理方式变得复杂。 让我们添加一个示例对此进行讨论。 在任何异步方法中，都可以在 finally 子句中使用 await 表达式。

使用 C# 6，还可以在 catch 表达式中使用 await。 这通常用于日志记录方案：

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

在 `catch` 和 `finally` 子句中添加 `await` 支持的实现细节可确保该行为与同步代码的行为一致。 当在 `catch` 或 `finally` 子句中执行的代码引发异常时，执行将在下一个外层块中查找合适的 `catch` 子句。 如果存在当前异常，则该异常将丢失。 `catch` 和 `finally` 子句中的 awaited 表达式也会发生同样的情况：搜索合适的 `catch`，并且当前异常（如果有）将丢失。  

> [!NOTE]
> 鉴于此行为，建议仔细编写 `catch` 和 `finally` 子句，避免引入新的异常。

## <a name="index-initializers"></a>索引初始化表达式

索引初始值设定项是提高集合初始值设定项与索引用途一致性的两个功能之一。 在早期版本的 C# 中，只能将集合初始值设定项用于序列样式集合，包括在键值对周围添加括号而得到 <xref:System.Collections.Generic.Dictionary%602>：

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

现在，可以将它们用于 <xref:System.Collections.Generic.Dictionary%602> 集合及类似的类型： 新语法支持使用索引分配到集合中：

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

此功能意味着，可以使用与多个版本中已有的序列容器语法类似的语法初始化关联容器。

## <a name="extension-add-methods-in-collection-initializers"></a>集合初始值设定项中的扩展 `Add` 方法

使集合初始化更容易的另一个功能是对 `Add` 方法使用扩展方法。 添加此功能的目的是进行 Visual Basic 的奇偶校验。 

如果自定义集合类的方法具有通过语义方式添加新项的名称，则此功能非常有用。

例如，请思考以下学生集合：

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` 方法会添加一个学生。 但它不遵循 `Add` 模式。
在以前的 C# 版本中，你不能对 `Enrollment` 对象使用集合初始值设定项：

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

现在可以，但前提是你创建将 `Add` 映射到 `Enroll` 的扩展方法：

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

你对此功能执行的操作是通过创建扩展方法，将把项添加到集合的任何方法映射到一个名为 `Add` 方法。

## <a name="improved-overload-resolution"></a>改进了重载解析

你可能不会注意到这最后一项功能。 在以前的一些构造中，以前版本的 C# 编译器可能会发现涉及 lambda 表达式的一些方法不明确。 请考虑此方法：

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

在早期版本的 C# 中，使用方法组语法调用该方法将失败：

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
早期的编译器无法正确区分 `Task.Run(Action)` 和 `Task.Run(Func<Task>())`。 在早期版本中，需要使用 lambda 表达式作为参数：

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 编译器正确地确定 `Task.Run(Func<Task>())` 是更好的选择。

### <a name="deterministic-compiler-output"></a>确定性的编译器选项

`-deterministic` 选项指示编译器为同一源文件的后续编译生成完全相同的输出程序集。

默认情况下，每个编译都生成唯一的输出内容。 编译器添加一个时间戳和一个随机生成的 GUID。 如果想按字节比较输出以确保各项生成之间的一致性，请使用此选项。

有关详细信息，请参阅 [-deterministic 编译器选项](../language-reference/compiler-options/deterministic-compiler-option.md)文章。
