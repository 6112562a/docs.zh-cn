---
title: 在 Visual Studio Code 中的 F# 入门
description: 了解如何使用 F# 与 Visual Studio Code 和 Ionide 插件套件。
ms.date: 05/28/2018
ms.openlocfilehash: e962be2796cf0d6eb90d459730659e492f864716
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "50192663"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>在 Visual Studio Code 中的 F# 入门

您可以编写 F# [Visual Studio Code](https://code.visualstudio.com)与[Ionide 插件](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)获取 IntelliSense 和基本代码更完美的跨平台的轻型集成开发环境 (IDE) 体验重构。 请访问[Ionide.io](http://ionide.io)若要了解有关该插件的详细信息。

若要开始，请确保已[F# 和 Ionide 插件正确安装](install-fsharp.md#install-f-with-visual-studio-code)。

## <a name="creating-your-first-project-with-ionide"></a>使用 Ionide 创建第一个项目

若要创建一个新的 F# 项目，请在 （可将其命名任意） 的新文件夹中打开 Visual Studio Code。

接下来，打开命令面板 (**视图 > 命令面板**) 并键入以下命令：

```
> F# new project
```

这由[伪造](https://github.com/fsharp-editing/Forge)项目。

> [!NOTE]
如果没有看到模板选项，请尝试通过运行以下命令在命令面板中刷新模板： `>F#: Refresh Project Templates`。

通过点击来选择"F#:: 新建项目" **Enter**。 这会转到下一步，即用于选择项目模板。

选取`classlib`模板，然后点击**Enter**。

接下来，选择一个目录来创建的项目中。 如果将其留空，则使用当前目录。

最后，在最后一步中的为项目命名。 使用 F# [Pascal 大小写](http://c2.com/cgi/wiki?PascalCase)项目名称。 本文使用`ClassLibraryDemo`作为名称。 已输入所需为你的项目的名称后, 命中**Enter**。

如果您遵循上一步，你会获得 Visual Studio 代码上的工作区的左侧具有以下出现：

1. F# 项目本身，其下方`ClassLibraryDemo`文件夹。
2. 添加通过包的正确的目录结构[ `Paket` ](https://fsprojects.github.io/Paket/)。
3. 跨平台生成的脚本[ `FAKE` ](https://fsharp.github.io/FAKE/)。
4. `paket.exe`可以提取包，并为您解决依赖项的可执行文件。
5. 一个`.gitignore`文件如果想要将此项目添加到基于 Git 的源代码管理。

## <a name="writing-some-code"></a>编写一些代码

打开*ClassLibraryDemo*文件夹。  您应看到以下文件：

1. `ClassLibraryDemo.fs`F# 实现文件与定义的类。
2. `ClassLibraryDemo.fsproj`用于生成此项目的 F# 项目文件。
3. `Script.fsx`加载的源文件的 F# 脚本文件。
4. `paket.references`指定项目依赖项的 paket 依存文件。

打开`Script.fsx`，并在它的末尾添加以下代码：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函数将一个单词转换到的窗体[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)。 下一步是对其使用 F# 交互式 (FSI) 进行评估。

突出显示整个函数 （它应为长达 11 行）。 一旦它被突出显示，保存**Alt**密钥并点击**Enter**。 您会注意到，下面的弹出窗口，它应显示类似如下：

![通过 Ionide F# Interactive 输出的示例](media/getting-started-vscode/vscode-fsi.png)

这做三件事：

1. 它启动了 FSI 进程。
2. 它通过金融服务业进程发送您突出显示的代码。
3. FSI 过程计算通过发送的代码。

因为您通过发送[函数](../language-reference/functions/index.md)，现在可以调用该函数使用 FSI ！ 在交互式窗口中，键入以下命令：

```fsharp
toPigLatin "banana";;
```

你应看到以下结果：

```fsharp
val it : string = "ananabay"
```

现在，让我们尝试使用作为第一个字母元音。 输入以下内容：

```fsharp
toPigLatin "apple";;
```

你应看到以下结果：

```fsharp
val it : string = "appleyay"
```

该函数似乎按预期方式工作。 祝贺你，只需在 Visual Studio Code 中编写第一个 F# 函数和计算使用 FSI ！

>[!NOTE]
您可能已经注意到，FSI 中的行结尾`;;`。 这是因为 FSI 可让你可以输入多行。 `;;`结束时，可让金融服务业知道何时完成代码。

## <a name="explaining-the-code"></a>解释代码

如果您不确定代码实际如何操作，下面是的分步说明。

如您所见，`toPigLatin`是一个函数，它接受作为其输入一个单词，并将其转换为该单词的 Pig Latin 表示形式。 此规则如下所示：

如果在 word 中的第一个字符以元音开头，添加到单词结尾"yay"。 如果它不以元音开头，将该第一个字符移动到单词结尾，并将"在"添加到它。

您可能已经注意到 FSI 中的以下：

```fsharp
val toPigLatin : word:string -> string
```

这表明`toPigLatin`是一个函数，采用`string`作为输入 (称为`word`)，并返回另一个`string`。 这称为[函数的类型签名](https://fsharpforfunandprofit.com/posts/function-signatures/)，F# 的是了解 F# 代码的关键的基本部分。 此外会发现这样如果您将鼠标悬停在 Visual Studio Code 中的函数。

在函数正文中，您会注意到两个不同的部分：

1. 内部函数，称为`isVowel`，，它确定如果给定的字符 (`c`) 通过检查与一个通过提供的模式匹配为元音[模式匹配](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)表达式，用以检查是否第一个字符为元音的元素，并返回值的所有输入字符构造基于 if 的第一个字符是元音还是失败：

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

流`toPigLatin`因此：

检查输入的单词的第一个字符是否元音。 如果是，将"yay"附加到单词结尾。 否则为将该第一个字符移动到单词结尾并将"在"添加到它。

还有一的最后一件事要注意这： 没有从与许多其他语言有不同的函数返回没有显式指令。 这是因为 F# 是基于表达式和函数的正文中的最后一个表达式是返回值。 因为`if..then..else`本身是一个表达式，正文`then`块或正文`else`块将根据输入值返回。

## <a name="moving-your-script-code-into-the-implementation-file"></a>将脚本代码移动到实现文件

在本文中前面部分所示编写 F# 代码的常见第一步： 编写初始函数并使用 FSI 以交互方式执行它。 这称为 REPL 驱动的开发，其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)代表"读取-评估-打印循环"。 它是实验功能，直到您看到的内容使用的好办法。

REPL 驱动开发的下一步是将工作代码移动到 F# 实现文件。 它然后，可编译的 F# 编译器为可执行程序集。

若要开始，请打开`ClassLibraryDemo.fs`。  您会注意到，一些代码中已存在。 请继续并删除类定义中，但请务必选中[ `namespace` ](../language-reference/namespaces.md)声明在顶部。

接下来，创建一个新[ `module` ](../language-reference/modules.md)调用`PigLatin`并复制`toPigLatin`函数导入到其这种情况下：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

接下来，打开`Script.fsx`文件，并删除整个`toPigLatin`函数，但请务必在文件中保留以下两行：

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

第一行所需的脚本加载 FSI `ClassLibraryDemo.fs`。 第二行是一种便于： 省略它是可选的但您将需要键入`open ClassLibraryDemo`如果你想要使程序 FSI 窗口中`ToPigLatin`纳入作用域的模块。

接下来，在 FSI 窗口中，调用与函数`PigLatin`前面定义的模块：

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

成功！ 获取与之前相同的结果，但现在从 F# 实现文件中加载。 此处的主要区别是，F# 源代码文件编译到可以不只是在 FSI 中任意位置，执行的程序集。

## <a name="summary"></a>总结

在本文中，你已了解：

1. 如何设置 Visual Studio Code 中通过 Ionide。
2. 如何使用 Ionide 创建第一个 F# 项目。
3. 如何使用 F# 脚本编写第一个 F# 函数中 Ionide 并执行在 FSI 中。
4. 如何将脚本代码迁移到 F# 源代码，然后从 FSI 调用该代码。

您现在能够编写更多 F# 代码使用 Visual Studio Code 和 Ionide。

## <a name="troubleshooting"></a>疑难解答

下面是几种方法可以对某些可能会遇到的问题进行故障排除：

1. 若要获取代码编辑功能 Ionide，F# 文件需要保存到磁盘，以及在 Visual Studio Code 工作区中处于打开状态的文件夹内。
2. 如果已对系统所做的更改，或使用打开的 Visual Studio Code 安装 Ionide 必备组件，请重新启动 Visual Studio Code。
3. 检查，可以使用 F# 编译器和 F# interactive 从命令行，而无需完全限定路径。 就可以通过键入`fsc`F# 编译器的命令行中和`fsi`或`fsharpi`Visual F# 工具在 Windows 和 Mac/Linux 上的 Mono 上分别。
4. 如果在项目目录中有无效字符，Ionide 可能无法工作。  如果出现这种情况，重命名你的项目目录。
5. 如果使用无 Ionide 命令，检查你[Visual Studio Code 的键绑定](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)看到如果你正在通过意外覆盖它们。
6. 如果你的计算机上将中断 Ionide 和以上均不是已修复问题，请尝试删除`ionide-fsharp`目录在计算机上重新安装该插件套件。

Ionide 是由 F# 社区成员处生成和维护的开放源代码项目。 请报告问题并随意在参与[Ionide VSCode: FSharp GitHub 存储库](https://github.com/ionide/ionide-vscode-fsharp)。

如果您有报告的问题，请按照[获取的日志报告的问题时要使用的说明](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。

此外可以通过 Ionide 开发人员和 F# 社区中的询问有关进一步的帮助[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。

## <a name="next-steps"></a>后续步骤

若要了解有关 F# 和语言的功能的详细信息，请查看[F# 教程](../tour.md)。
