---
title: C# 中的数字 - C# 教程简介
description: 通过浏览数字类型、其属性和方法了解 C#。
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: e9d8b09bde6e87edf9f483c0c296dbb256343f58
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774023"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="fae26-103">处理 C\# 中的整数和浮点数</span><span class="sxs-lookup"><span data-stu-id="fae26-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="fae26-104">本教程以交互方式介绍了 C# 中的数字类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="fae26-105">你将编写少量的代码，然后编译并运行这些代码。</span><span class="sxs-lookup"><span data-stu-id="fae26-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="fae26-106">本教程包含一系列课程，介绍了 C# 中的数字和数学运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="fae26-107">这些课程介绍了 C# 语言的基础知识。</span><span class="sxs-lookup"><span data-stu-id="fae26-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="fae26-108">本教程要求你有一台可用于开发的计算机。</span><span class="sxs-lookup"><span data-stu-id="fae26-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="fae26-109">.NET 教程 [Hello World 10 分钟入门](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)介绍了如何在 Windows、Linux 或 macOS 上设置本地开发环境。</span><span class="sxs-lookup"><span data-stu-id="fae26-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="fae26-110">[熟悉开发工具](local-environment.md)不仅简要概述了将用到的命令，还收录了详细信息链接。</span><span class="sxs-lookup"><span data-stu-id="fae26-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="fae26-111">探索整数数学运算</span><span class="sxs-lookup"><span data-stu-id="fae26-111">Explore integer math</span></span>

<span data-ttu-id="fae26-112">创建名为 numbers-quickstart  的目录。</span><span class="sxs-lookup"><span data-stu-id="fae26-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="fae26-113">将新建的目录设为当前目录，并运行 `dotnet new console -n NumbersInCSharp -o .`。</span><span class="sxs-lookup"><span data-stu-id="fae26-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="fae26-114">在常用编辑器中，打开 Program.cs  ，并将行 `Console.WriteLine("Hello World!");` 替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="fae26-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="fae26-115">通过在命令窗口中键入 `dotnet run` 运行此代码。</span><span class="sxs-lookup"><span data-stu-id="fae26-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="fae26-116">刚刚看到的是一种基本的整数数学运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="fae26-117">`int` 类型表示整数  （零、正整数或负整数）。</span><span class="sxs-lookup"><span data-stu-id="fae26-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="fae26-118">使用 `+` 符号执行加法运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="fae26-119">其他常见的整数数学运算包括：</span><span class="sxs-lookup"><span data-stu-id="fae26-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="fae26-120">`-`：减法运算</span><span class="sxs-lookup"><span data-stu-id="fae26-120">`-` for subtraction</span></span>
- <span data-ttu-id="fae26-121">`*`：乘法运算</span><span class="sxs-lookup"><span data-stu-id="fae26-121">`*` for multiplication</span></span>
- <span data-ttu-id="fae26-122">`/`：除法运算</span><span class="sxs-lookup"><span data-stu-id="fae26-122">`/` for division</span></span>

<span data-ttu-id="fae26-123">首先，探索这些不同类型的运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-123">Start by exploring those different operations.</span></span> <span data-ttu-id="fae26-124">在写入 `c` 值的行之后添加以下行：</span><span class="sxs-lookup"><span data-stu-id="fae26-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="fae26-125">通过在命令窗口中键入 `dotnet run` 运行此代码。</span><span class="sxs-lookup"><span data-stu-id="fae26-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="fae26-126">如果愿意，也可以尝试在同一行中执行多个数学运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="fae26-127">例如，请尝试 `c = a + b - 12 * 17;`。</span><span class="sxs-lookup"><span data-stu-id="fae26-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="fae26-128">允许混合使用变量和常数。</span><span class="sxs-lookup"><span data-stu-id="fae26-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="fae26-129">在探索 C#（或任何编程语言）的过程中，可能会在编写代码时犯错。</span><span class="sxs-lookup"><span data-stu-id="fae26-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="fae26-130">编译器  会发现并报告这些错误。</span><span class="sxs-lookup"><span data-stu-id="fae26-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="fae26-131">如果输出中包含错误消息，请仔细比对示例代码和你的窗口中的代码，看看哪些需要纠正。</span><span class="sxs-lookup"><span data-stu-id="fae26-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="fae26-132">这样做有助于了解 C# 代码结构。</span><span class="sxs-lookup"><span data-stu-id="fae26-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="fae26-133">你已完成第一步。</span><span class="sxs-lookup"><span data-stu-id="fae26-133">You've finished the first step.</span></span> <span data-ttu-id="fae26-134">开始进入下一部分前，先将当前代码移到单独的方法中。</span><span class="sxs-lookup"><span data-stu-id="fae26-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="fae26-135">这样一来，可以更轻松地开始处理新示例。</span><span class="sxs-lookup"><span data-stu-id="fae26-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="fae26-136">将 `Main` 方法重命名为 `WorkingWithIntegers`，并编写调用 `WorkingWithIntegers` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="fae26-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="fae26-137">完成后，代码应如下所示：</span><span class="sxs-lookup"><span data-stu-id="fae26-137">When you finish, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="fae26-138">探索运算顺序</span><span class="sxs-lookup"><span data-stu-id="fae26-138">Explore order of operations</span></span>

<span data-ttu-id="fae26-139">注释掉对 `WorkingWithIntegers()` 的调用。</span><span class="sxs-lookup"><span data-stu-id="fae26-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="fae26-140">在本节中，它会在你工作时使输出变得不那么杂乱：</span><span class="sxs-lookup"><span data-stu-id="fae26-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="fae26-141">`//` 在 C# 中启动  注释。</span><span class="sxs-lookup"><span data-stu-id="fae26-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="fae26-142">注释是你想要保留在源代码中但不能作为代码执行的任何文本。</span><span class="sxs-lookup"><span data-stu-id="fae26-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="fae26-143">编译器不会从注释中生成任何可执行代码。</span><span class="sxs-lookup"><span data-stu-id="fae26-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="fae26-144">C# 语言使用与数学运算规则一致的规则，定义不同数学运算的优先级。</span><span class="sxs-lookup"><span data-stu-id="fae26-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="fae26-145">乘法和除法的优先级高于加法和减法。</span><span class="sxs-lookup"><span data-stu-id="fae26-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="fae26-146">将以下代码添加到 `Main` 方法，然后执行 `dotnet run` 进行探索：</span><span class="sxs-lookup"><span data-stu-id="fae26-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="fae26-147">输出结果表明，乘法先于加法执行。</span><span class="sxs-lookup"><span data-stu-id="fae26-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="fae26-148">可以在要优先执行的一个或多个运算前后添加括号，从而强制改变运算顺序。</span><span class="sxs-lookup"><span data-stu-id="fae26-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="fae26-149">添加以下行并再次运行：</span><span class="sxs-lookup"><span data-stu-id="fae26-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="fae26-150">通过组合多个不同的运算，进一步探索运算顺序。</span><span class="sxs-lookup"><span data-stu-id="fae26-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="fae26-151">在 `Main` 方法底部添加类似以下行的内容。</span><span class="sxs-lookup"><span data-stu-id="fae26-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="fae26-152">重试 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="fae26-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="fae26-153">可能已注意到，整数有一个非常有趣的行为。</span><span class="sxs-lookup"><span data-stu-id="fae26-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="fae26-154">整数除法始终生成整数结果，即使预期结果有小数或分数部分也是如此。</span><span class="sxs-lookup"><span data-stu-id="fae26-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="fae26-155">如果你没有注意到此行为，请在 `Main` 方法结束时试运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="fae26-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="fae26-156">再次键入 `dotnet run`，看看结果如何。</span><span class="sxs-lookup"><span data-stu-id="fae26-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="fae26-157">继续之前，让我们获取你在本节编写的所有代码并放在新的方法中。</span><span class="sxs-lookup"><span data-stu-id="fae26-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="fae26-158">调用新方法 `OrderPrecedence`。</span><span class="sxs-lookup"><span data-stu-id="fae26-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="fae26-159">最后应以与下面类似的代码结束：</span><span class="sxs-lookup"><span data-stu-id="fae26-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="fae26-160">探索整数运算精度和限值</span><span class="sxs-lookup"><span data-stu-id="fae26-160">Explore integer precision and limits</span></span>

<span data-ttu-id="fae26-161">在上一个示例中，整数除法截断了结果。</span><span class="sxs-lookup"><span data-stu-id="fae26-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="fae26-162">可以使用取模  运算符（即 `%` 字符）计算余数  。</span><span class="sxs-lookup"><span data-stu-id="fae26-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="fae26-163">在 `Main` 方法中试用以下代码：</span><span class="sxs-lookup"><span data-stu-id="fae26-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="fae26-164">C# 整数类型不同于数学上的整数的另一点是，`int` 类型有最小限值和最大限值。</span><span class="sxs-lookup"><span data-stu-id="fae26-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="fae26-165">将此代码添加到 `Main` 方法，看看这些限制的运行机制：</span><span class="sxs-lookup"><span data-stu-id="fae26-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="fae26-166">如果运算生成的值超过这些限值，则会出现下溢  或溢出  的情况。</span><span class="sxs-lookup"><span data-stu-id="fae26-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="fae26-167">答案似乎是从一个限值覆盖到另一个限值的范围。</span><span class="sxs-lookup"><span data-stu-id="fae26-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="fae26-168">例如，将以下两行添加到 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="fae26-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="fae26-169">可以看到，答案非常接近最小（负）整数。</span><span class="sxs-lookup"><span data-stu-id="fae26-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="fae26-170">与 `min + 2` 相同。</span><span class="sxs-lookup"><span data-stu-id="fae26-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="fae26-171">加法运算会让整数溢出  允许的值。</span><span class="sxs-lookup"><span data-stu-id="fae26-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="fae26-172">答案是一个非常大的负数，因为溢出从最大整数值覆盖回最小整数值。</span><span class="sxs-lookup"><span data-stu-id="fae26-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="fae26-173">如果 `int` 类型无法满足需求，还会用到限值和精度不同的其他数字类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="fae26-174">接下来，将探索这些类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-174">Let's explore those next.</span></span>

<span data-ttu-id="fae26-175">让我们再一次将你在本节编写的代码移到一个单独的方法中。</span><span class="sxs-lookup"><span data-stu-id="fae26-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="fae26-176">将其命名为 `TestLimits`。</span><span class="sxs-lookup"><span data-stu-id="fae26-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="fae26-177">使用双精度类型</span><span class="sxs-lookup"><span data-stu-id="fae26-177">Work with the double type</span></span>

<span data-ttu-id="fae26-178">`double` 数字类型表示双精度浮点数。</span><span class="sxs-lookup"><span data-stu-id="fae26-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="fae26-179">这些词可能是第一次听说。</span><span class="sxs-lookup"><span data-stu-id="fae26-179">Those terms may be new to you.</span></span> <span data-ttu-id="fae26-180">浮点  数可用于表示数量级可能非常大或非常小的非整数。</span><span class="sxs-lookup"><span data-stu-id="fae26-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="fae26-181">双精度  意味着存储这些数字时使用的精度高于单精度  。</span><span class="sxs-lookup"><span data-stu-id="fae26-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="fae26-182">在新式计算机上，使用双精度数字比使用单精度数字更为常见。</span><span class="sxs-lookup"><span data-stu-id="fae26-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="fae26-183">接下来，将探索双精度类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-183">Let's explore.</span></span> <span data-ttu-id="fae26-184">添加以下代码并查看结果：</span><span class="sxs-lookup"><span data-stu-id="fae26-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="fae26-185">可以看到，答案商包含小数部分。</span><span class="sxs-lookup"><span data-stu-id="fae26-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="fae26-186">试试对双精度类型使用更复杂一点的表达式：</span><span class="sxs-lookup"><span data-stu-id="fae26-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="fae26-187">双精度值的范围远大于整数值。</span><span class="sxs-lookup"><span data-stu-id="fae26-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="fae26-188">在当前已编写的代码下方试运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="fae26-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="fae26-189">打印出来的这些值用科学记数法表示。</span><span class="sxs-lookup"><span data-stu-id="fae26-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="fae26-190">`E` 左侧为有效数字。</span><span class="sxs-lookup"><span data-stu-id="fae26-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="fae26-191">右侧为是 10 的 n 次幂。</span><span class="sxs-lookup"><span data-stu-id="fae26-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="fae26-192">与数学上的十进制数字一样，C# 中的双精度值可能会有四舍五入误差。</span><span class="sxs-lookup"><span data-stu-id="fae26-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="fae26-193">试运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="fae26-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="fae26-194">众所周知，`0.3` 循环小数与 `1/3` 并不完全相等。</span><span class="sxs-lookup"><span data-stu-id="fae26-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="fae26-195">***挑战***</span><span class="sxs-lookup"><span data-stu-id="fae26-195">***Challenge***</span></span>

<span data-ttu-id="fae26-196">尝试使用 `double` 类型执行其他的大小数、乘法和除法运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="fae26-197">尝试执行更复杂的运算。</span><span class="sxs-lookup"><span data-stu-id="fae26-197">Try more complicated calculations.</span></span>

<span data-ttu-id="fae26-198">花了一些时间应对挑战之后，获取已编写的代码并放在一个新方法中。</span><span class="sxs-lookup"><span data-stu-id="fae26-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="fae26-199">将新方法命名为 `WorkWithDoubles`。</span><span class="sxs-lookup"><span data-stu-id="fae26-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="fae26-200">使用固定点类型</span><span class="sxs-lookup"><span data-stu-id="fae26-200">Work with fixed point types</span></span>

<span data-ttu-id="fae26-201">大家已学习了 C# 中的基本数字类型，即整数和双精度。</span><span class="sxs-lookup"><span data-stu-id="fae26-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="fae26-202">下面将介绍另一种需要了解的类型，即 `decimal` 类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="fae26-203">`decimal` 类型的范围较小，但精度高于 `double`。</span><span class="sxs-lookup"><span data-stu-id="fae26-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="fae26-204">“固定点”一词  意味着，十进制小数点（或二进制小数点）不会移动。</span><span class="sxs-lookup"><span data-stu-id="fae26-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="fae26-205">让我们来实际操作一下：</span><span class="sxs-lookup"><span data-stu-id="fae26-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="fae26-206">可以看到，范围小于 `double` 类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="fae26-207">通过试运行以下代码，可以看到十进制类型的精度更高：</span><span class="sxs-lookup"><span data-stu-id="fae26-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="fae26-208">数字中的 `M` 后缀指明了常数应如何使用 `decimal` 类型。</span><span class="sxs-lookup"><span data-stu-id="fae26-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="fae26-209">可以看到，使用十进制类型执行数学运算时，十进制小数点右侧的数字更多。</span><span class="sxs-lookup"><span data-stu-id="fae26-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="fae26-210">***挑战***</span><span class="sxs-lookup"><span data-stu-id="fae26-210">***Challenge***</span></span>

<span data-ttu-id="fae26-211">至此，大家已了解不同的数字类型。请编写代码来计算圆面积（其中，半径为 2.50 厘米）。</span><span class="sxs-lookup"><span data-stu-id="fae26-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="fae26-212">请注意，圆面积是用半径的平方乘以 PI 进行计算。</span><span class="sxs-lookup"><span data-stu-id="fae26-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="fae26-213">小提示：.NET 包含 PI 常数 <xref:System.Math.PI?displayProperty=nameWithType>，可用于相应的值计算。</span><span class="sxs-lookup"><span data-stu-id="fae26-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="fae26-214">你应获得 19 和 20 之间的答案。</span><span class="sxs-lookup"><span data-stu-id="fae26-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="fae26-215">要查看你的答案，可以[查看 GitHub 上的完成示例代码](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="fae26-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="fae26-216">如果需要，可以试用一些其他公式。</span><span class="sxs-lookup"><span data-stu-id="fae26-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="fae26-217">已完成“C# 中的数字”快速入门教程。</span><span class="sxs-lookup"><span data-stu-id="fae26-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="fae26-218">可以在自己的开发环境中继续学习[分支和循环](branches-and-loops-local.md)快速入门教程。</span><span class="sxs-lookup"><span data-stu-id="fae26-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="fae26-219">可以参阅下面的主题，详细了解 C# 中的数字：</span><span class="sxs-lookup"><span data-stu-id="fae26-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="fae26-220">整型数值类型</span><span class="sxs-lookup"><span data-stu-id="fae26-220">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="fae26-221">浮点型数值类型</span><span class="sxs-lookup"><span data-stu-id="fae26-221">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="fae26-222">内置数值转换</span><span class="sxs-lookup"><span data-stu-id="fae26-222">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
