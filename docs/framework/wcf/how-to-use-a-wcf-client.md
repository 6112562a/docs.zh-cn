---
title: 教程：使用 Windows Communication Foundation 客户端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928886"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="cdb14-102">教程：使用 Windows Communication Foundation 客户端</span><span class="sxs-lookup"><span data-stu-id="cdb14-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="cdb14-103">本教程介绍创建基本 Windows Communication Foundation （WCF）应用程序所需的五个任务中的最后一个。</span><span class="sxs-lookup"><span data-stu-id="cdb14-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="cdb14-104">有关教程的概述，请参阅[教程：开始 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb14-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="cdb14-105">创建并配置 Windows Communication Foundation （WCF）代理后，您可以创建一个客户端实例并编译该客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="cdb14-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="cdb14-106">然后，你可以使用它来与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="cdb14-106">You then use it to communicate with the WCF service.</span></span> 

<span data-ttu-id="cdb14-107">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="cdb14-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cdb14-108">添加代码以使用 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="cdb14-109">测试 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="cdb14-110">添加代码以使用 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="cdb14-110">Add code to use the WCF client</span></span>

<span data-ttu-id="cdb14-111">客户端代码执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="cdb14-111">The client code does the following steps:</span></span>

- <span data-ttu-id="cdb14-112">实例化 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="cdb14-113">从生成的代理调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="cdb14-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="cdb14-114">完成操作调用后关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="cdb14-115">从**GettingStartedClient**项目中打开**Program.cs**或**Module1**文件，并将其代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="cdb14-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="cdb14-116">请注意导入C# `Imports` 的`GettingStartedClient.ServiceReference1`（适用于 Visual）或（适用 Visual Basic）语句。 `using`</span><span class="sxs-lookup"><span data-stu-id="cdb14-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="cdb14-117">此语句将导入 Visual Studio 生成的带有**添加服务引用**函数的代码。</span><span class="sxs-lookup"><span data-stu-id="cdb14-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="cdb14-118">此代码实例化 WCF 代理，并调用计算器服务公开的每个服务操作。</span><span class="sxs-lookup"><span data-stu-id="cdb14-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="cdb14-119">然后，它会关闭代理并结束程序。</span><span class="sxs-lookup"><span data-stu-id="cdb14-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="cdb14-120">测试 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="cdb14-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="cdb14-121">从 Visual Studio 测试应用程序</span><span class="sxs-lookup"><span data-stu-id="cdb14-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="cdb14-122">保存并生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="cdb14-122">Save and build the solution.</span></span>

2. <span data-ttu-id="cdb14-123">选择**GettingStartedLib**文件夹，然后从快捷菜单中选择 "**设为启动项目**"。</span><span class="sxs-lookup"><span data-stu-id="cdb14-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="cdb14-124">从 "**启动项目**" 中，从下拉列表中选择 " **GettingStartedLib** "，然后选择 "**运行**" 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="cdb14-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="cdb14-125">在命令提示符下测试应用程序</span><span class="sxs-lookup"><span data-stu-id="cdb14-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="cdb14-126">以管理员身份打开命令提示符，然后导航到你的 Visual Studio 解决方案目录。</span><span class="sxs-lookup"><span data-stu-id="cdb14-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span> 

2. <span data-ttu-id="cdb14-127">若要启动该服务：输入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。</span><span class="sxs-lookup"><span data-stu-id="cdb14-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="cdb14-128">启动客户端：打开另一个命令提示符，导航到 Visual Studio 解决方案目录，然后输入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。</span><span class="sxs-lookup"><span data-stu-id="cdb14-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="cdb14-129">*GettingStartedHost*生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cdb14-129">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="cdb14-130">*GettingStartedClient*生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cdb14-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="cdb14-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cdb14-131">Next steps</span></span>

<span data-ttu-id="cdb14-132">你现在已经完成了 WCF 入门教程中的所有任务。</span><span class="sxs-lookup"><span data-stu-id="cdb14-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="cdb14-133">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="cdb14-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="cdb14-134">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="cdb14-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cdb14-135">添加代码以使用 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="cdb14-136">测试 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="cdb14-136">Test the WCF client.</span></span>

<span data-ttu-id="cdb14-137">如果在任何步骤中遇到问题或错误，请按照故障排除一文中的步骤进行修复。</span><span class="sxs-lookup"><span data-stu-id="cdb14-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cdb14-138">排查 WCF 入门教程</span><span class="sxs-lookup"><span data-stu-id="cdb14-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
