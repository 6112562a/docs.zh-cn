---
title: 限制并行 ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715910"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="c6669-102">限制并行 ForEach</span><span class="sxs-lookup"><span data-stu-id="c6669-102">Throttled Parallel ForEach</span></span>

<span data-ttu-id="c6669-103">`ThrottleParallelForEach` 活动类似于 <xref:System.Activities.Statements.ParallelForEach%601> 活动，不同之处在于前者允许设置并发系数来限制要执行的并发分支的数目。</span><span class="sxs-lookup"><span data-stu-id="c6669-103">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="c6669-104">`ThrottleParallelForEach` 活动派生自 <xref:System.Activities.NativeActivity>，因为该活动需要对其他活动（子活动）进行计划，并且只有通过 <xref:System.Activities.NativeActivityContext> 类才能对此进行访问。</span><span class="sxs-lookup"><span data-stu-id="c6669-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="c6669-105">项目</span><span class="sxs-lookup"><span data-stu-id="c6669-105">Projects</span></span>

|<span data-ttu-id="c6669-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="c6669-106">**ProjectName**</span></span>|<span data-ttu-id="c6669-107">**描述**</span><span class="sxs-lookup"><span data-stu-id="c6669-107">**Description**</span></span>|<span data-ttu-id="c6669-108">**主文件**</span><span class="sxs-lookup"><span data-stu-id="c6669-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="c6669-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="c6669-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="c6669-110">包含 `ThrottledParallelForEach` 活动及其设计器。</span><span class="sxs-lookup"><span data-stu-id="c6669-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="c6669-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="c6669-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="c6669-112">`ThrottledParallelForEach` 活动定义。</span><span class="sxs-lookup"><span data-stu-id="c6669-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="c6669-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="c6669-113">CodeTestClient</span></span>|<span data-ttu-id="c6669-114">示例客户端应用程序，通过使用命令性代码的 `ThrottledParallelForEach` 来配置和运行工作流。</span><span class="sxs-lookup"><span data-stu-id="c6669-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="c6669-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="c6669-115">Program.cs</span></span><br /><br /> <span data-ttu-id="c6669-116">定义和运行示例工作流的实例。</span><span class="sxs-lookup"><span data-stu-id="c6669-116">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="c6669-117">使用此示例</span><span class="sxs-lookup"><span data-stu-id="c6669-117">To use this sample</span></span>

1. <span data-ttu-id="c6669-118">使用 Visual Studio 2010 打开 ThrottledParallelForEach 文件。</span><span class="sxs-lookup"><span data-stu-id="c6669-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="c6669-119">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="c6669-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="c6669-120">若要运行解决方案，请按 F5。</span><span class="sxs-lookup"><span data-stu-id="c6669-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6669-121">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c6669-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6669-122">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c6669-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c6669-123">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c6669-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6669-124">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c6669-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
