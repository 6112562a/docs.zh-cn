---
title: 在一段时间后取消异步任务 (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204344"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="e8287-102">在一段时间后取消异步任务 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8287-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="e8287-103">如果不希望等待操作结束，可使用 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 方法在一段时间后取消异步操作。</span><span class="sxs-lookup"><span data-stu-id="e8287-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="e8287-104">此方法会计划取消未在 `CancelAfter` 表达式指定的时间段内完成的任何关联任务。</span><span class="sxs-lookup"><span data-stu-id="e8287-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="e8287-105">此示例添加到[取消异步任务或任务列表 (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)中开发的代码，以下载网站列表并显示每个网站的内容长度。</span><span class="sxs-lookup"><span data-stu-id="e8287-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="e8287-106">若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e8287-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="e8287-107">下载示例</span><span class="sxs-lookup"><span data-stu-id="e8287-107">Download the example</span></span>

<span data-ttu-id="e8287-108">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。</span><span class="sxs-lookup"><span data-stu-id="e8287-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e8287-109">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e8287-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e8287-110">在菜单栏上，依次选择  “文件” >   “打开” >   “项目/解决方案”。</span><span class="sxs-lookup"><span data-stu-id="e8287-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e8287-111">在“打开项目”  对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningCS 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="e8287-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="e8287-112">在“解决方案资源管理器”  中，打开“CancelAfterTime”  项目的快捷菜单，然后选择“设为启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="e8287-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e8287-113">按  F5 键运行此项目。</span><span class="sxs-lookup"><span data-stu-id="e8287-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="e8287-114">（或者，按 Ctrl  +F5  运行该项目，无需调试）。</span><span class="sxs-lookup"><span data-stu-id="e8287-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="e8287-115">多次运行程序以验证输出是否显示所有网站的输出、不显示网站的输出或显示某些网站的输出。</span><span class="sxs-lookup"><span data-stu-id="e8287-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="e8287-116">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="e8287-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="e8287-117">生成示例</span><span class="sxs-lookup"><span data-stu-id="e8287-117">Build the example</span></span>

<span data-ttu-id="e8287-118">本主题中的示例添加到[取消异步任务或任务列表 (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)中开发的项目，以取消任务列表。</span><span class="sxs-lookup"><span data-stu-id="e8287-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="e8287-119">该示例使用相同的 UI，但未显示使用“取消”  按钮。</span><span class="sxs-lookup"><span data-stu-id="e8287-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="e8287-120">若要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“CancelAListOfTasks”  作为“启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="e8287-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="e8287-121">将此主题中的更改添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="e8287-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="e8287-122">若要指定将任务标记为取消之前的最长时间，请将对 `CancelAfter` 的调用添加到 `startButton_Click`，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="e8287-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="e8287-123">新增内容标有星号。</span><span class="sxs-lookup"><span data-stu-id="e8287-123">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
    }
    catch (OperationCanceledException)
    {
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }

    cts = null;
}
```

 <span data-ttu-id="e8287-124">多次运行程序以验证输出是否显示所有网站的输出、不显示网站的输出或显示某些网站的输出。</span><span class="sxs-lookup"><span data-stu-id="e8287-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="e8287-125">以下输出为示例。</span><span class="sxs-lookup"><span data-stu-id="e8287-125">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="e8287-126">完整示例</span><span class="sxs-lookup"><span data-stu-id="e8287-126">Complete example</span></span>

<span data-ttu-id="e8287-127">下列代码是示例的 MainWindow.xaml.cs 文件的完整文本。</span><span class="sxs-lookup"><span data-stu-id="e8287-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="e8287-128">对添加到此示例的元素进行了星号标记。</span><span class="sxs-lookup"><span data-stu-id="e8287-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="e8287-129">请注意，必须为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="e8287-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="e8287-130">可以从 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。</span><span class="sxs-lookup"><span data-stu-id="e8287-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace CancelAfterTime
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="e8287-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8287-131">See also</span></span>

- [<span data-ttu-id="e8287-132">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8287-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="e8287-133">演练：使用 Async 和 Await 访问 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="e8287-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="e8287-134">取消异步任务或任务列表 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8287-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="e8287-135">微调异步应用程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8287-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="e8287-136">异步示例：微调应用程序</span><span class="sxs-lookup"><span data-stu-id="e8287-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
