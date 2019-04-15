---
title: 开始使用F#在 Visual Studio 中
description: 了解如何使用F#使用 Visual Studio。
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331905"
---
# <a name="get-started-with-f-in-visual-studio"></a>开始使用F#在 Visual Studio 中

F#和视觉对象F#工具支持在 Visual Studio IDE 中。

若要开始，请确保已[Visual Studio 安装与F# ](install-fsharp.md#install-f-with-visual-studio)。

## <a name="creating-a-console-application"></a>创建控制台应用程序

Visual Studio 中最基本的项目之一是控制台应用程序。  以下是使用方法。  打开 Visual Studio 后：

1. 上**文件**菜单，依次指向**新建**，然后选择**项目**。

2. 在新建项目对话框中下,**模板**，你应看到**Visual F#** 。  选择此选项可显示F#模板。

3. 选择任一 **.NET Core 控制台应用程序**或**控制台应用**。

3. 选择**好**按钮以创建F#项目 ！  现在应看到F#解决方案资源管理器中的项目。

## <a name="writing-your-code"></a>编写代码

通过编写一些代码首先让我们开始吧。  请确保`Program.fs`文件已打开，，然后将其内容替换为以下：

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

在前面的代码示例，一个函数`square`具有已定义接受名为输入`x`并将其本身乘以。  因为F#使用[类型推理](../language-reference/type-inference.md)的类型`x`不需要指定。  F#编译器了解有效，乘法的类型，并将分配到的类型`x`具体取决于`square`调用。  如果您悬停`square`，则应查看以下信息：

```
val square: x:int -> int
```

这是所谓的函数的类型签名。  它可以读取如下："正方形是一个函数，它采用名为整数 x，并生成一个整数"。  请注意，编译器提供`square``int`类型现在-这是因为乘法不是泛型跨*所有*类型，但而不是跨一组已关闭的类型是泛型。  F#编译器中选取`int`在此点，但它将调整类型签名如果调用`square`与其他输入类型，如`float`。

另一个函数`main`，定义，则这用修饰`EntryPoint`属性告知F#编译器的执行程序时，应从这里开始。  它遵循的约定与其他[C 样式编程语言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中的命令行参数可以传递给此函数，并返回一个整数代码 (通常`0`)。

在我们调用此函数是`square`函数的参数和`12`。  F#编译器然后将分配的类型`square`要`int -> int`(即，一个函数，它采用`int`，并生成`int`)。  对调用`printfn`是格式化的打印函数使用类似于 C 样式编程语言，它们分别对应于格式字符串中指定的参数的格式字符串，然后将打印结果和一个新行。

## <a name="running-your-code"></a>运行代码

可以运行该代码并查看结果，通过按**Ctrl**+**F5**。  这不进行调试直接运行该程序，并允许您以查看结果。  或者，你可以选择**调试**顶级菜单项在 Visual Studio 中，然后选择**启动但不调试**。

现在应看到以下输出到控制台窗口的 Visual Studio 中：

```
12 squared is 144!
```

祝贺你！  你已创建你的第一个F#在 Visual Studio 中，编写的项目F#函数输出的结果调用的函数，并运行项目以查看部分结果。

## <a name="next-steps"></a>后续步骤

如果你尚未这样做，请查看[概览F# ](../tour.md)，其中介绍了一些核心功能F#语言。  它将为您提供的某些功能的概述F#，并提供足够的代码示例，你可以将复制到 Visual Studio 并运行。  此外，还有一些有用的外部资源，您可以使用，在演示[F#指南](../index.md)。

## <a name="see-also"></a>请参阅

- [F# 概览](../tour.md)
- [F#语言参考](../language-reference/index.md)
- [类型推理](../language-reference/type-inference.md)
- [符号和运算符参考](../language-reference/symbol-and-operator-reference/index.md)
