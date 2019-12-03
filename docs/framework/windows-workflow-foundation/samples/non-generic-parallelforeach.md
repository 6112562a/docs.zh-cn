---
title: 非泛型 ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715648"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="caf23-102">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="caf23-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="caf23-103">的工具箱中附带了一组控制流活动，其中包括可用来循环访问 <xref:System.Activities.Statements.ParallelForEach%601> 集合的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="caf23-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="caf23-104"><xref:System.Activities.Statements.ParallelForEach%601> 要求其 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> 属性为 <xref:System.Collections.Generic.IEnumerable%601>类型。</span><span class="sxs-lookup"><span data-stu-id="caf23-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="caf23-105">这将阻止用户循环访问实现 <xref:System.Collections.Generic.IEnumerable%601> 接口（例如，<xref:System.Collections.ArrayList>）的数据结构。</span><span class="sxs-lookup"><span data-stu-id="caf23-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="caf23-106">非泛型版本的 <xref:System.Activities.Statements.ParallelForEach%601> 没有这一需求，不过与此对应的代价是，需要更复杂的运行时来确保集合中的值类型的兼容性。</span><span class="sxs-lookup"><span data-stu-id="caf23-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="caf23-107">此示例演示如何实现非泛型的 <xref:System.Activities.Statements.ParallelForEach%601> 活动及其设计器。</span><span class="sxs-lookup"><span data-stu-id="caf23-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="caf23-108">此活动可用于循环访问 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="caf23-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="caf23-109">ParallelForEach 活动</span><span class="sxs-lookup"><span data-stu-id="caf23-109">ParallelForEach activity</span></span>

<span data-ttu-id="caf23-110">C#/VB `foreach` 语句枚举集合的元素，对集合中的每个元素执行嵌入语句。</span><span class="sxs-lookup"><span data-stu-id="caf23-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="caf23-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 等效活动为 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="caf23-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="caf23-112"><xref:System.Activities.Statements.ForEach%601> 活动包含一个值列表和一个主体。</span><span class="sxs-lookup"><span data-stu-id="caf23-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="caf23-113">在运行时，将循环访问此列表，并对列表中的每个值执行主体。</span><span class="sxs-lookup"><span data-stu-id="caf23-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="caf23-114"><xref:System.Activities.Statements.ParallelForEach%601> 具有一个 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>，以便在 <xref:System.Activities.Statements.ParallelForEach%601> 的计算返回 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 的情况下，`true` 活动能够及早完成。</span><span class="sxs-lookup"><span data-stu-id="caf23-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="caf23-115">在每次迭代完成之后，将计算 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>。</span><span class="sxs-lookup"><span data-stu-id="caf23-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="caf23-116">对于大多数情况，此活动的泛型版本应为首选解决方案，因为它涵盖了应使用此活动的大多数方案，并且提供编译时类型检查。</span><span class="sxs-lookup"><span data-stu-id="caf23-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="caf23-117">非泛型版本可用于循环访问实现非泛型 <xref:System.Collections.IEnumerable> 接口的类型。</span><span class="sxs-lookup"><span data-stu-id="caf23-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="caf23-118">类定义</span><span class="sxs-lookup"><span data-stu-id="caf23-118">Class definition</span></span>

<span data-ttu-id="caf23-119">下面的代码示例显示非泛型 `ParallelForEach` 活动的定义。</span><span class="sxs-lookup"><span data-stu-id="caf23-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="caf23-120">Body （可选） </span><span class="sxs-lookup"><span data-stu-id="caf23-120">Body (optional)</span></span>\
<span data-ttu-id="caf23-121"><xref:System.Activities.ActivityAction> 类型的 <xref:System.Object>，将对集合中的每个元素执行它。</span><span class="sxs-lookup"><span data-stu-id="caf23-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="caf23-122">通过单个元素的 Argument 属性将其传递到 Body。</span><span class="sxs-lookup"><span data-stu-id="caf23-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="caf23-123">值（可选） </span><span class="sxs-lookup"><span data-stu-id="caf23-123">Values (optional)</span></span>\
<span data-ttu-id="caf23-124">循环访问的元素集合。</span><span class="sxs-lookup"><span data-stu-id="caf23-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="caf23-125">在运行时确保所有集合元素为兼容类型。</span><span class="sxs-lookup"><span data-stu-id="caf23-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="caf23-126">CompletionCondition （可选） </span><span class="sxs-lookup"><span data-stu-id="caf23-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="caf23-127">在任何迭代完成之后，将计算 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="caf23-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="caf23-128">如果其计算结果为 `true`，则取消已安排的挂起的迭代。</span><span class="sxs-lookup"><span data-stu-id="caf23-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="caf23-129">如果未设置此属性，则 Branches 集合中的所有活动都将执行，直至完成为止。</span><span class="sxs-lookup"><span data-stu-id="caf23-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="caf23-130">使用 ParallelForEach 的示例</span><span class="sxs-lookup"><span data-stu-id="caf23-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="caf23-131">下面的代码演示如何在应用程序中使用 ParallelForEach 活动。</span><span class="sxs-lookup"><span data-stu-id="caf23-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="caf23-132">ParallelForEach 设计器</span><span class="sxs-lookup"><span data-stu-id="caf23-132">ParallelForEach designer</span></span>

<span data-ttu-id="caf23-133">此示例的活动设计器的外观与为内置 <xref:System.Activities.Statements.ParallelForEach%601> 活动提供的设计器的外观相似。</span><span class="sxs-lookup"><span data-stu-id="caf23-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="caf23-134">设计器将显示在工具箱中的 "**示例**"、"**非泛型" 活动**类别。</span><span class="sxs-lookup"><span data-stu-id="caf23-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="caf23-135">设计器在 "工具箱" 中名为 " **ParallelForEachWithBodyFactory** "，因为活动在工具箱中公开了一个 <xref:System.Activities.Presentation.IActivityTemplateFactory>，该活动使用正确配置的 <xref:System.Activities.ActivityAction>创建活动。</span><span class="sxs-lookup"><span data-stu-id="caf23-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="caf23-136">运行示例</span><span class="sxs-lookup"><span data-stu-id="caf23-136">To run the sample</span></span>

1. <span data-ttu-id="caf23-137">将您选择的项目设置为解决方案的启动项目。</span><span class="sxs-lookup"><span data-stu-id="caf23-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="caf23-138">**CodeTestClient**演示如何使用代码使用活动。</span><span class="sxs-lookup"><span data-stu-id="caf23-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="caf23-139">**DesignerTestClient**演示如何在设计器中使用活动。</span><span class="sxs-lookup"><span data-stu-id="caf23-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="caf23-140">生成并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="caf23-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caf23-141">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="caf23-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="caf23-142">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="caf23-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="caf23-143">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="caf23-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="caf23-144">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="caf23-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
