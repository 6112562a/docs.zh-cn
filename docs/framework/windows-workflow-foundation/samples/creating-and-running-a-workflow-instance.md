---
title: 创建和运行工作流实例
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016046"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="514f5-102">创建和运行工作流实例</span><span class="sxs-lookup"><span data-stu-id="514f5-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="514f5-103">此示例演示如何运行工作流实例。</span><span class="sxs-lookup"><span data-stu-id="514f5-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="514f5-104">它演示如何以同步方式和异步方式执行这一操作。</span><span class="sxs-lookup"><span data-stu-id="514f5-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="514f5-105">演示</span><span class="sxs-lookup"><span data-stu-id="514f5-105">Demonstrates</span></span>

<span data-ttu-id="514f5-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="514f5-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="514f5-107">讨论</span><span class="sxs-lookup"><span data-stu-id="514f5-107">Discussion</span></span>

<span data-ttu-id="514f5-108">此示例的第一部分使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。</span><span class="sxs-lookup"><span data-stu-id="514f5-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="514f5-109">这是执行工作流的最基本方法。</span><span class="sxs-lookup"><span data-stu-id="514f5-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="514f5-110">使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 执行的工作流以同步方式执行。</span><span class="sxs-lookup"><span data-stu-id="514f5-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="514f5-111">该示例的第二部分使用 <xref:System.Activities.WorkflowApplication> 类。</span><span class="sxs-lookup"><span data-stu-id="514f5-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="514f5-112">利用 <xref:System.Activities.WorkflowApplication>，您可以对每个实例进行更多控制，包括与正在运行的工作流进行交互的能力和异步运行工作流的能力。</span><span class="sxs-lookup"><span data-stu-id="514f5-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="514f5-113">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="514f5-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="514f5-114">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="514f5-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="514f5-115">如果此目录不存在, 请参阅[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)以下载所有 Windows Communication Foundation (wcf) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。</span><span class="sxs-lookup"><span data-stu-id="514f5-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="514f5-116">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="514f5-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="514f5-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="514f5-117">See also</span></span>

- [<span data-ttu-id="514f5-118">使用 WorkflowInvoker 和 WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="514f5-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
