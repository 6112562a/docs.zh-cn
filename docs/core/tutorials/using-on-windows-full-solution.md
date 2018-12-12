---
title: 在 Windows 上，使用 Visual Studio 2017 生成完整的 .NET Core 解决方案
description: 了解如何在 Windows 上的 Visual Studio 2017 中生成完整的 .NET Core 解决方案。
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: b3e466511fcae447f5bb54b83f13b25bc90c6539
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149947"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="2f29e-103">在 Windows 上，使用 Visual Studio 2017 生成完整的 .NET Core 解决方案</span><span class="sxs-lookup"><span data-stu-id="2f29e-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="2f29e-104">Visual Studio 2017 提供用于开发 .NET Core 应用程序的功能全面的开发环境。</span><span class="sxs-lookup"><span data-stu-id="2f29e-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="2f29e-105">本文档中的过程介绍了构建典型的 .NET Core 解决方案所需的步骤，包含可重用库、测试以及使用第三方库。</span><span class="sxs-lookup"><span data-stu-id="2f29e-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="2f29e-106">系统必备</span><span class="sxs-lookup"><span data-stu-id="2f29e-106">Prerequisites</span></span>

<span data-ttu-id="2f29e-107">请按照[先决条件页](../windows-prerequisites.md)上的说明更新环境。</span><span class="sxs-lookup"><span data-stu-id="2f29e-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="2f29e-108">仅使用 .NET Core 项目的解决方案</span><span class="sxs-lookup"><span data-stu-id="2f29e-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="2f29e-109">编写库</span><span class="sxs-lookup"><span data-stu-id="2f29e-109">Writing the library</span></span>

1. <span data-ttu-id="2f29e-110">在 Visual Studio 中，依次选择 **“文件”**、 **“新建”**、 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="2f29e-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="2f29e-111">在“新建项目”对话框中，展开“Visual C#”节点并选择“.NET Standard”节点，然后选择“类库(.NET Standard)”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> <span data-ttu-id="2f29e-112">这将创建一个 .NET Standard 库，该库面向 .NET Core 及支持 [.NET Standard](../../standard/net-standard.md) 版本 2.0 的任何其他 .NET 实现。</span><span class="sxs-lookup"><span data-stu-id="2f29e-112">This creates a .NET Standard library that targets .NET Core as well as any other .NET implementation that supports version 2.0 of the [.NET Standard](../../standard/net-standard.md).</span></span>

2. <span data-ttu-id="2f29e-113">将项目命名为“Library”，将解决方案命名为“Golden”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="2f29e-114">保持选中“为解决方案创建目录”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="2f29e-115">单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="2f29e-115">Click **OK**.</span></span>

3. <span data-ttu-id="2f29e-116">在“解决方案资源管理器”中，打开“依赖项”节点的上下文菜单，并选择“管理 NuGet 包”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="2f29e-117">选择“nuget.org”作为“包源”，并选择“浏览”选项卡。浏找到 **Newtonsoft.Json**。</span><span class="sxs-lookup"><span data-stu-id="2f29e-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="2f29e-118">单击“安装”，然后接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="2f29e-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="2f29e-119">现在，包应该在“依赖项/NuGet”下显示并自动还原。</span><span class="sxs-lookup"><span data-stu-id="2f29e-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="2f29e-120">将 `Class1.cs` 文件重命名为 `Thing.cs`。</span><span class="sxs-lookup"><span data-stu-id="2f29e-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="2f29e-121">接受类的重命名。</span><span class="sxs-lookup"><span data-stu-id="2f29e-121">Accept the rename of the class.</span></span> <span data-ttu-id="2f29e-122">添加方法：`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="2f29e-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="2f29e-123">在 **“生成”** 菜单上，选择 **“生成解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="2f29e-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="2f29e-124">应可以准确无误地生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="2f29e-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="2f29e-125">编写测试项目</span><span class="sxs-lookup"><span data-stu-id="2f29e-125">Writing the test project</span></span>

1. <span data-ttu-id="2f29e-126">在“解决方案资源管理器”中，打开“解决方案”节点的上下文菜单，然后依次选择“添加”、“新建项目”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="2f29e-127">在“新建项目”对话框中的“Visual C#/.NET Core”下选择“单元测试项目 (.NET Core)”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="2f29e-128">将它命名为“TestLibrary”，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="2f29e-129">在“TestLibrary”项目中，打开“依赖项”节点的上下文菜单，选择“添加引用”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="2f29e-130">单击“项目”，然后勾选库项目并单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="2f29e-131">这会将测试项目中的引用添加到库中。</span><span class="sxs-lookup"><span data-stu-id="2f29e-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="2f29e-132">将 `UnitTest1.cs` 文件重命名为 `LibraryTests.cs` 并接受类重命名。</span><span class="sxs-lookup"><span data-stu-id="2f29e-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="2f29e-133">将 `using Library;` 添加到文件顶部，并将`TestMethod1` 方法替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="2f29e-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="2f29e-134">现在，应该可以生成解决方案了。</span><span class="sxs-lookup"><span data-stu-id="2f29e-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="2f29e-135">在“测试”菜单上，依次选择“Windows”和“测试资源管理器”，将测试资源管理器窗口植入工作区。</span><span class="sxs-lookup"><span data-stu-id="2f29e-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="2f29e-136">几秒钟后，`ThingGetsObjectValFromNumber` 测试应在测试资源管理器中显示。</span><span class="sxs-lookup"><span data-stu-id="2f29e-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="2f29e-137">选择 **“全部运行”**。</span><span class="sxs-lookup"><span data-stu-id="2f29e-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="2f29e-138">测试应该会通过。</span><span class="sxs-lookup"><span data-stu-id="2f29e-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="2f29e-139">编写控制台应用</span><span class="sxs-lookup"><span data-stu-id="2f29e-139">Writing the console app</span></span>

1. <span data-ttu-id="2f29e-140">在“解决方案资源管理器”中，打开解决方案的上下文菜单，添加新的**控制台应用 (.NET Core)** 项目。</span><span class="sxs-lookup"><span data-stu-id="2f29e-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="2f29e-141">将其命名为“App”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-141">Name it "App".</span></span>

2. <span data-ttu-id="2f29e-142">在 **App** 项目中，打开“依赖项”节点的上下文菜单，依次选择“添加”**和**“引用”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="2f29e-143">在“引用管理器”对话框中，选中“项目”、“解决方案”节点下的“库”，然后单击“确定”</span><span class="sxs-lookup"><span data-stu-id="2f29e-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="2f29e-144">打开 **App** 节点的上下文菜单，选择“设置为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="2f29e-145">这确保了按住 F5 或 Ctrl+F5 时可启动控制台应用。</span><span class="sxs-lookup"><span data-stu-id="2f29e-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="2f29e-146">打开 `Program.cs` 文件，将 `using Library;` 指令添加到文件顶部，然后将 `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` 添加到 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="2f29e-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="2f29e-147">在刚添加的行后设置一个断点。</span><span class="sxs-lookup"><span data-stu-id="2f29e-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="2f29e-148">按 F5 运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="2f29e-148">Press F5 to run the application.</span></span>

   <span data-ttu-id="2f29e-149">应用程序应正确生成并命中断点。</span><span class="sxs-lookup"><span data-stu-id="2f29e-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="2f29e-150">应该也可检查应用程序输出“The answer is 42.”。</span><span class="sxs-lookup"><span data-stu-id="2f29e-150">You should also be able to check that the application output "The answer is 42.".</span></span>
