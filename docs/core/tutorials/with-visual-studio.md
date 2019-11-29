---
title: 使用 Visual Studio 2017 生成 C# .NET Core Hello World 应用程序
description: 了解如何使用 Visual Studio 2017 生成简单的 C# .NET Core 控制台应用程序。
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cc7d78006998b79fe9d522e71883ce1af817c051
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428559"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="9e8c7-103">在 Visual Studio 2017 中使用 .NET Core SDK 生成 C# Hello World 应用程序</span><span class="sxs-lookup"><span data-stu-id="9e8c7-103">Build a C# Hello World application with the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="9e8c7-104">本文将逐步介绍如何在 Visual Studio 2017 中使用 C# 生成、调试和发布一个简单的 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-104">This article provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="9e8c7-105">Visual Studio 2017 提供了功能全面的开发环境，可用于生成 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="9e8c7-106">只要应用程序没有平台专属依赖项，应用程序就可以在 .NET Core 的任何目标平台上和安装了 .NET Core 的任何系统上运行。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e8c7-107">系统必备</span><span class="sxs-lookup"><span data-stu-id="9e8c7-107">Prerequisites</span></span>

<span data-ttu-id="9e8c7-108">已安装“.NET Core 跨平台开发”工作负载的 [Visual Studio 2017 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-108">[Visual Studio 2017 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="9e8c7-109">可以使用 .NET Core 2.1 或更高版本开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-109">You can develop your app with .NET Core 2.1 or later versions.</span></span>

<span data-ttu-id="9e8c7-110">有关详细信息，请参阅 [.NET Core 依赖项和要求](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio)一文。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-110">For more information, see the [.NET Core dependencies and requirements](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio)article.</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="9e8c7-111">简单的“Hello World”应用程序</span><span class="sxs-lookup"><span data-stu-id="9e8c7-111">A simple Hello World application</span></span>

<span data-ttu-id="9e8c7-112">首先创建简单的“Hello World”控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="9e8c7-113">请执行这些步骤：</span><span class="sxs-lookup"><span data-stu-id="9e8c7-113">Follow these steps:</span></span>

1. <span data-ttu-id="9e8c7-114">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-114">Launch Visual Studio.</span></span> <span data-ttu-id="9e8c7-115">从菜单栏中选择“文件”   > “新建”   > “项目”  。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9e8c7-116">在“新项目”  对话框中，依次选择“Visual C#”  和“.NET Core”  节点。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-116">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="9e8c7-117">然后，选择“控制台应用程序(.NET Core)”  项目模板。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="9e8c7-118">在“名称”  文本框中，键入“HelloWorld”。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="9e8c7-119">选择“确定”  按钮。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-119">Select the **OK** button.</span></span>

   ![选择了“控制台应用”的“新建项目”对话框](./media/with-visual-studio/visual-studio-new-project.png)

1. <span data-ttu-id="9e8c7-121">Visual Studio 使用模板创建项目。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="9e8c7-122">C# .NET Core 控制台应用程序模板会自动定义类 `Program` 和一个需要将 <xref:System.String> 数组用作自变量的方法 `Main`。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-122">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="9e8c7-123">`Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="9e8c7-124">*args* 数组中包含在应用程序启动时提供的所有命令行自变量。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio 和新建的 HelloWorld 项目](./media/with-visual-studio/visual-studio-main-window.png)

   <span data-ttu-id="9e8c7-126">用于创建简单的“Hello World”应用程序的模板。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="9e8c7-127">它通过调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法在控制台窗口中</span><span class="sxs-lookup"><span data-stu-id="9e8c7-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="9e8c7-128">显示文本字符串“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-128">in the console window.</span></span> <span data-ttu-id="9e8c7-129">现在，选择工具栏上含绿色箭头的“HelloWorld”  按钮，可以在调试模式下运行程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="9e8c7-130">如果这样操作，控制台窗口只在较短的时间内可见，然后就会关闭。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="9e8c7-131">这是因为在执行 `Main` 方法中的单个语句后，`Main` 方法和应用程序将立即终止。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="9e8c7-132">若要在应用程序关闭控制台窗口前将其暂停，请在调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法后立即添加下列代码：</span><span class="sxs-lookup"><span data-stu-id="9e8c7-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   <span data-ttu-id="9e8c7-133">此代码会提示用户按任意键，然后在用户按键前暂停程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="9e8c7-134">在菜单栏中，选择“生成”   > “生成解决方案”  。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="9e8c7-135">这会将程序编译成一种中间语言 (IL)，然后由实时 (JIT) 编译器转换成二进制代码。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="9e8c7-136">选择工具栏上含绿色箭头的“HelloWorld”  按钮，从而运行程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![控制台窗口，其中显示 Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="9e8c7-138">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="9e8c7-139">改进“Hello World”应用程序</span><span class="sxs-lookup"><span data-stu-id="9e8c7-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="9e8c7-140">改进应用程序，提示用户输入名字，并将其与日期和时间一同显示。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-140">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="9e8c7-141">若要修改和测试程序，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9e8c7-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="9e8c7-142">在代码窗口中，在紧跟 `static void Main(string[] args)` 代码行的左括号之后和第一个右花括号之前，输入以下 C# 代码：</span><span class="sxs-lookup"><span data-stu-id="9e8c7-142">Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing curly bracket:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="9e8c7-143">此代码将替换 `Main` 方法的内容。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-143">This code replaces the contents of the `Main` method.</span></span>

   ![Visual Studio Program c-sharp 文件，含更新后 Main 方法](./media/with-visual-studio/visual-csharp-code-window.png)

   <span data-ttu-id="9e8c7-145">此代码在控制台中显示“What is your name?”，</span><span class="sxs-lookup"><span data-stu-id="9e8c7-145">This code displays "What is your name?"</span></span> <span data-ttu-id="9e8c7-146">然后等待用户输入字符串并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="9e8c7-147">它将此字符串存储到名为 `name` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="9e8c7-148">它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="9e8c7-149">最后，使用[内插字符串](../../csharp/language-reference/tokens/interpolated.md)在控制台窗口中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-149">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="9e8c7-150">依次选择 **“生成”**  >  **“生成解决方案”** ，编译此程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="9e8c7-151">选择工具栏上的绿色箭头、按 F5 或选择“调试”   > “启动调试”  菜单项，在 Visual Studio 的调试模式下运行程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="9e8c7-152">出现提示时，输入名称并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![控制台窗口，含已修改程序的输出](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="9e8c7-154">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-154">Press any key to close the console window.</span></span>

<span data-ttu-id="9e8c7-155">现已创建并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-155">You've created and run your application.</span></span> <span data-ttu-id="9e8c7-156">若要开发专业应用程序，仍需要执行一些其他步骤，才可发布应用程序：</span><span class="sxs-lookup"><span data-stu-id="9e8c7-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="9e8c7-157">有关调试应用程序的信息，请参阅[使用 Visual Studio 2017 调试 .NET Core Hello World 应用程序](debugging-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-157">For information on debugging your application, see [Debug your .NET Core Hello World application using Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="9e8c7-158">若要了解如何开发和发布可发行版应用程序，请参阅[使用 Visual Studio 2017 发布 NET Core Hello World 应用程序](publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-158">For information on developing and publishing a distributable version of your application, see [Publish your .NET Core Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-articles"></a><span data-ttu-id="9e8c7-159">相关文章</span><span class="sxs-lookup"><span data-stu-id="9e8c7-159">Related articles</span></span>

<span data-ttu-id="9e8c7-160">还可以使用 Visual Studio 2017 生成 .NET Core 类库，而不是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-160">Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017.</span></span> <span data-ttu-id="9e8c7-161">有关分步说明，请参阅[使用 Visual Studio 2017 生成 C# .NET Core 类库](library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-161">For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).</span></span>

<span data-ttu-id="9e8c7-162">还可以使用 [Visual Studio Code](https://code.visualstudio.com/)（可供下载的代码编辑器）开发在 Mac、Linux 和 Windows 上运行的 .NET Core 控制台应用。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-162">You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor.</span></span> <span data-ttu-id="9e8c7-163">有关分步教程，请参阅 [Visual Studio Code 入门](with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="9e8c7-163">For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md).</span></span>
