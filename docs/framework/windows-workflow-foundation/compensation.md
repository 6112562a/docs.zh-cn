---
title: 补偿
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935431"
---
# <a name="compensation"></a><span data-ttu-id="edd4b-102">补偿</span><span class="sxs-lookup"><span data-stu-id="edd4b-102">Compensation</span></span>
<span data-ttu-id="edd4b-103">Windows Workflow Foundation （WF）中的补偿是一种机制，通过该机制，可以在发生后续失败时撤消或补偿之前完成的工作。</span><span class="sxs-lookup"><span data-stu-id="edd4b-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="edd4b-104">本节介绍如何在工作流中使用补偿。</span><span class="sxs-lookup"><span data-stu-id="edd4b-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="edd4b-105">补偿与事务</span><span class="sxs-lookup"><span data-stu-id="edd4b-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="edd4b-106">通过事务可以将多个操作合并为单个工作单元。</span><span class="sxs-lookup"><span data-stu-id="edd4b-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="edd4b-107">使用事务时，如果事务进程中任何部分出现错误，则你的应用程序可以中止（回滚）在事务内执行的所有更改。</span><span class="sxs-lookup"><span data-stu-id="edd4b-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="edd4b-108">但是，如果工作长时间运行，使用事务可能不合适。</span><span class="sxs-lookup"><span data-stu-id="edd4b-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="edd4b-109">例如，一个作为工作流实现的差旅计划应用程序。</span><span class="sxs-lookup"><span data-stu-id="edd4b-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="edd4b-110">该工作流的步骤可能包含预订航班、等待经理批准，然后支付机票费用。</span><span class="sxs-lookup"><span data-stu-id="edd4b-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="edd4b-111">这个过程会花费几天的时间，不适合将预订航班步骤和支付机票费用步骤合并到同一事务中。</span><span class="sxs-lookup"><span data-stu-id="edd4b-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="edd4b-112">在此类方案中，如果在以后的处理中出现失败，可以使用补偿来撤消工作流的预订步骤。</span><span class="sxs-lookup"><span data-stu-id="edd4b-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edd4b-113">本主题介绍工作流中的补偿。</span><span class="sxs-lookup"><span data-stu-id="edd4b-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="edd4b-114">有关工作流中事务的详细信息， 请参阅[事务](workflow-transactions.md)和 <xref:System.Activities.Statements.TransactionScope>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="edd4b-115">有关事务的详细信息，请<xref:System.Transactions?displayProperty=nameWithType>参阅<xref:System.Transactions.Transaction?displayProperty=nameWithType>和。</span><span class="sxs-lookup"><span data-stu-id="edd4b-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="edd4b-116">使用 CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="edd4b-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="edd4b-117"><xref:System.Activities.Statements.CompensableActivity> 是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的核心补偿活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="edd4b-118">将执行可能需要补偿的工作的所有活动放置到 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中。</span><span class="sxs-lookup"><span data-stu-id="edd4b-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="edd4b-119">在本示例中，将购买机票的预订步骤放置到 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中，并且将取消预订放置到 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中。</span><span class="sxs-lookup"><span data-stu-id="edd4b-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="edd4b-120">紧接着在工作流中的 <xref:System.Activities.Statements.CompensableActivity> 之后是两个活动，即等待经理批准，然后完成购买机票的步骤。</span><span class="sxs-lookup"><span data-stu-id="edd4b-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="edd4b-121">如果在 <xref:System.Activities.Statements.CompensableActivity> 成功完成之后某个错误条件导致要取消工作流，则会安排 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 处理程序中的活动并且取消相应的航班。</span><span class="sxs-lookup"><span data-stu-id="edd4b-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="edd4b-122">下面的示例是 XAML 形式的工作流。</span><span class="sxs-lookup"><span data-stu-id="edd4b-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="edd4b-123">在调用工作流时，将下面的输出显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="edd4b-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="edd4b-124">**ReserveFlight票证已保留。**</span><span class="sxs-lookup"><span data-stu-id="edd4b-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="edd4b-125">**ManagerApproval已收到经理批准。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="edd4b-126">**PurchaseFlight已购买票证。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="edd4b-127">**工作流已成功完成，状态为：闭.**</span><span class="sxs-lookup"><span data-stu-id="edd4b-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
> <span data-ttu-id="edd4b-128">本主题中的示例活动（例如 `ReserveFlight`）显示将其名称和用途显示到控制台，以帮助说明在发生补偿时执行这些活动的顺序。</span><span class="sxs-lookup"><span data-stu-id="edd4b-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="edd4b-129">默认的工作流补偿</span><span class="sxs-lookup"><span data-stu-id="edd4b-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="edd4b-130">默认情况下，如果工作流被取消，则会对已成功完成以及尚未确认或补偿的任何可补偿的活动运行补偿逻辑。</span><span class="sxs-lookup"><span data-stu-id="edd4b-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edd4b-131">确认后，将无法再调用活动的补偿。 <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="edd4b-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="edd4b-132">本节的后面部分介绍确认过程。</span><span class="sxs-lookup"><span data-stu-id="edd4b-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="edd4b-133">在本示例中，预订航班之后，但在经理批准步骤之前引发了一个异常。</span><span class="sxs-lookup"><span data-stu-id="edd4b-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="edd4b-134">此示例是 XAML 形式的工作流。</span><span class="sxs-lookup"><span data-stu-id="edd4b-134">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="edd4b-135">当调用工作流时，将由 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的主机应用程序处理模拟错误条件异常，工作流被取消并调用补偿逻辑。</span><span class="sxs-lookup"><span data-stu-id="edd4b-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="edd4b-136">**ReserveFlight票证已保留。**</span><span class="sxs-lookup"><span data-stu-id="edd4b-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="edd4b-137">**SimulatedErrorCondition引发 ApplicationException。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="edd4b-138">**工作流未处理异常：**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="edd4b-139">**ApplicationException：工作流中的模拟错误条件。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="edd4b-140">**CancelFlight票证已取消。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="edd4b-141">**工作流已成功完成，状态为：放弃.**</span><span class="sxs-lookup"><span data-stu-id="edd4b-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="edd4b-142">取消和 CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="edd4b-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="edd4b-143">如果 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 中的活动未完成并且取消了该活动，则执行 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 中的活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edd4b-144">如果 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的活动未完成并且取消了该活动，则只调用 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="edd4b-145">如果 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的活动已成功完成并且随后对该活动调用了补偿，则只执行 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="edd4b-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 为工作流作者创造了机会来提供任何适当的取消逻辑。</span><span class="sxs-lookup"><span data-stu-id="edd4b-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="edd4b-147">在下面的示例中，在执行 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 期间引发异常，然后调用 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="edd4b-148">此示例是 XAML 形式的工作流</span><span class="sxs-lookup"><span data-stu-id="edd4b-148">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="edd4b-149">当调用工作流时，将由 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 中的宿主应用程序处理模拟错误条件异常，工作流被取消并调用 <xref:System.Activities.Statements.CompensableActivity> 的取消逻辑。</span><span class="sxs-lookup"><span data-stu-id="edd4b-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="edd4b-150">在此示例中，补偿逻辑和取消逻辑具有不同的目的。</span><span class="sxs-lookup"><span data-stu-id="edd4b-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="edd4b-151">如果成功完成了 <xref:System.Activities.Statements.CompensableActivity.Body%2A>，则意味着对这张信用卡已收取费用并且航班已预订，因此补偿应撤消这两个步骤。</span><span class="sxs-lookup"><span data-stu-id="edd4b-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="edd4b-152">（在此示例中，如果自动取消航班，将取消信用卡收费。）但是，如果取消 <xref:System.Activities.Statements.CompensableActivity>，则意味着 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 未完成，因此 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 的逻辑需要能够确定如何最好地处理取消。</span><span class="sxs-lookup"><span data-stu-id="edd4b-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="edd4b-153">在此示例中，<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 取消信用卡收费，但由于 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最后一个活动，因此它不会尝试取消航班。</span><span class="sxs-lookup"><span data-stu-id="edd4b-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="edd4b-154">因为 `ReserveFlight` 是 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 中的最后一个活动，所以，如果它已经成功完成，则 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 应该已完成并可能没有取消。</span><span class="sxs-lookup"><span data-stu-id="edd4b-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="edd4b-155">**ChargeCreditCard:为航班付费。**</span><span class="sxs-lookup"><span data-stu-id="edd4b-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="edd4b-156">**SimulatedErrorCondition引发 ApplicationException。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="edd4b-157">**工作流未处理异常：**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="edd4b-158">**ApplicationException：工作流中的模拟错误条件。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="edd4b-159">**CancelCreditCard:取消信用卡收费。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="edd4b-160">**工作流已成功完成，状态为：放弃.**</span><span class="sxs-lookup"><span data-stu-id="edd4b-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="edd4b-161">有关取消的详细信息，请参阅[取消](modeling-cancellation-behavior-in-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="edd4b-161">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="edd4b-162">使用 Compensate 活动的显式补偿</span><span class="sxs-lookup"><span data-stu-id="edd4b-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="edd4b-163">在上一节中，我们介绍了隐式补偿。</span><span class="sxs-lookup"><span data-stu-id="edd4b-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="edd4b-164">隐式补偿可能适合于简单方案，但如果在安排补偿处理时需要更多显式控件，则可以使用 <xref:System.Activities.Statements.Compensate> 活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="edd4b-165">若要使用 <xref:System.Activities.Statements.Compensate> 活动启动补偿过程，请使用需要补偿的 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="edd4b-166">可以使用 <xref:System.Activities.Statements.Compensate> 活动在尚未确认或补偿的任何已完成的 <xref:System.Activities.Statements.CompensableActivity> 上启动补偿。</span><span class="sxs-lookup"><span data-stu-id="edd4b-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="edd4b-167">例如，可以在 <xref:System.Activities.Statements.Compensate> 活动的 <xref:System.Activities.Statements.TryCatch.Catches%2A> 部分中或完成 <xref:System.Activities.Statements.TryCatch> 之后的任何时间使用 <xref:System.Activities.Statements.CompensableActivity> 活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="edd4b-168">在本示例中，在 <xref:System.Activities.Statements.Compensate> 活动的 <xref:System.Activities.Statements.TryCatch.Catches%2A> 部分中使用了 <xref:System.Activities.Statements.TryCatch> 活动以反转 <xref:System.Activities.Statements.CompensableActivity> 的操作。</span><span class="sxs-lookup"><span data-stu-id="edd4b-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="edd4b-169">此示例是 XAML 形式的工作流。</span><span class="sxs-lookup"><span data-stu-id="edd4b-169">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="edd4b-170">在调用工作流时，将下面的输出显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="edd4b-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="edd4b-171">**ReserveFlight票证已保留。**</span><span class="sxs-lookup"><span data-stu-id="edd4b-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="edd4b-172">**SimulatedErrorCondition引发 ApplicationException。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="edd4b-173">**CancelFlight票证已取消。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="edd4b-174">**工作流已成功完成，状态为：闭.**</span><span class="sxs-lookup"><span data-stu-id="edd4b-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="edd4b-175">确认补偿</span><span class="sxs-lookup"><span data-stu-id="edd4b-175">Confirming Compensation</span></span>  
 <span data-ttu-id="edd4b-176">默认情况下，可以在完成活动之后的任何时间对可补偿的活动进行补偿。</span><span class="sxs-lookup"><span data-stu-id="edd4b-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="edd4b-177">但是，在某些情况下，这可能不太合适。</span><span class="sxs-lookup"><span data-stu-id="edd4b-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="edd4b-178">在上一个示例中，对预订机票的补偿是取消预订。</span><span class="sxs-lookup"><span data-stu-id="edd4b-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="edd4b-179">但是，在航程完成之后，此补偿步骤将不再有效。</span><span class="sxs-lookup"><span data-stu-id="edd4b-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="edd4b-180">确认可补偿的活动会调用由 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 指定的活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="edd4b-181">该操作的一个可能用处是允许释放对于执行补偿非常必要的所有资源。</span><span class="sxs-lookup"><span data-stu-id="edd4b-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="edd4b-182">在确认可补偿的活动之后，不能再对该活动进行补偿，并且如果尝试该操作，则会引发一个 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="edd4b-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="edd4b-183">工作流成功完成之后，会按相反的完成顺序确认成功完成的所有未确认以及未补偿的可补偿活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="edd4b-184">在本示例中，预订航班、购买机票并完成，然后确认可补偿的活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="edd4b-185">若要确认某个 <xref:System.Activities.Statements.CompensableActivity>，请使用 <xref:System.Activities.Statements.Confirm> 活动并指定要确认的 <xref:System.Activities.Statements.CompensationToken> 的 <xref:System.Activities.Statements.CompensableActivity>。</span><span class="sxs-lookup"><span data-stu-id="edd4b-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="edd4b-186">此示例是 XAML 形式的工作流。</span><span class="sxs-lookup"><span data-stu-id="edd4b-186">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="edd4b-187">在调用工作流时，将下面的输出显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="edd4b-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="edd4b-188">**ReserveFlight票证已保留。**</span><span class="sxs-lookup"><span data-stu-id="edd4b-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="edd4b-189">**ManagerApproval已收到经理批准。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="edd4b-190">**PurchaseFlight已购买票证。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="edd4b-191">**TakeFlight航班已完成。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="edd4b-192">**ConfirmFlight已采用航班，无法进行补偿。**  </span><span class="sxs-lookup"><span data-stu-id="edd4b-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="edd4b-193">**工作流已成功完成，状态为：闭.**</span><span class="sxs-lookup"><span data-stu-id="edd4b-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="edd4b-194">嵌套补偿活动</span><span class="sxs-lookup"><span data-stu-id="edd4b-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="edd4b-195">可以将 <xref:System.Activities.Statements.CompensableActivity> 放置到另一个 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 的 <xref:System.Activities.Statements.CompensableActivity> 部分中。</span><span class="sxs-lookup"><span data-stu-id="edd4b-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="edd4b-196"><xref:System.Activities.Statements.CompensableActivity> 不能放置于另一个 <xref:System.Activities.Statements.CompensableActivity> 的处理程序中。</span><span class="sxs-lookup"><span data-stu-id="edd4b-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="edd4b-197">在父级完成取消、确认或补偿操作前，确保在 <xref:System.Activities.Statements.CompensableActivity> 父级取消、确认或补偿时，所有已成功完成的和尚未得到确认或补偿的子级可补偿活动必须得到确认和补偿是该父级的责任。</span><span class="sxs-lookup"><span data-stu-id="edd4b-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="edd4b-198">如果不对此进行显式建模，在该父级接收到取消或补偿信号时，<xref:System.Activities.Statements.CompensableActivity> 将隐式补偿可补偿的子级活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="edd4b-199">如果父级收到了确认信号，则该父级将隐式确认可补偿的子级活动。</span><span class="sxs-lookup"><span data-stu-id="edd4b-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="edd4b-200">如果用于处理取消、确认或补偿的逻辑在父 <xref:System.Activities.Statements.CompensableActivity> 的处理程序中被显式建模，则未显式处理的所有子级都将被隐式确定。</span><span class="sxs-lookup"><span data-stu-id="edd4b-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd4b-201">请参阅</span><span class="sxs-lookup"><span data-stu-id="edd4b-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
