---
title: Windows Communication Foundation로 메시지 큐
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 541ea23e6748242db57661ceda8e1fedecb66884
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747118"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="59b20-102">Windows Communication Foundation로 메시지 큐</span><span class="sxs-lookup"><span data-stu-id="59b20-102">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="59b20-103">此示例演示消息队列（MSMQ）应用程序如何将 MSMQ 消息发送到 Windows Communication Foundation （WCF）服务。</span><span class="sxs-lookup"><span data-stu-id="59b20-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="59b20-104">이 서비스는 자체적으로 호스트되는 콘솔 애플리케이션으로서 이를 사용하여 서비스에서 대기된 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="59b20-105">서비스 계약은 `IOrderProcessor`이며, 이는 큐에 사용하기에 적합한 단방향 서비스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="59b20-106">MSMQ 메시지에는 동작 헤더가 없기 때문에 여러 MSMQ 메시지를 작업 계약에 자동으로 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="59b20-107">따라서 작업 계약이 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="59b20-108">서비스에 대해 둘 이상의 작업 계약을 정의하려는 경우 애플리케이션은 디스패치할 작업 계약을 결정하는 데 사용할 수 있는 MSMQ 메시지의 헤더와 관련된 정보(예: 레이블 또는 correlationID)를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="59b20-109">MSMQ 메시지에는 작업 계약의 여러 매개 변수에 매핑되는 헤더에 대한 정보는 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="59b20-110">매개 변수의 형식은 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`)이고, 여기에는 기본 MSMQ 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="59b20-111"><xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) 클래스의 "T" 형식은 MSMQ 메시지 본문으로 serialize되는 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="59b20-112">이 샘플에서는 `PurchaseOrder` 형식이 MSMQ 메시지 본문으로 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="59b20-113">다음 샘플 코드에서는 주문 처리 서비스의 서비스 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-113">The following sample code shows the service contract of the order processing service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="59b20-114">서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-114">The service is self hosted.</span></span> <span data-ttu-id="59b20-115">MSMQ를 사용하는 경우에는 사용되는 큐를 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="59b20-116">수동으로 또는 코드를 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-116">This can be done manually or through code.</span></span> <span data-ttu-id="59b20-117">이 샘플에서 서비스는 큐가 있는지 확인하고 필요한 경우 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="59b20-118">큐 이름은 구성 파일에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-118">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="59b20-119">다음 샘플 코드에서와 같이 서비스는 <xref:System.ServiceModel.ServiceHost>를 위한 `OrderProcessorService`를 만들고 엽니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="59b20-120">다음 샘플 구성에서 보여 주는 것처럼 MSMQ 큐 이름은 구성 파일의 appSettings 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="59b20-121">큐 이름은 로컬 컴퓨터에 점(.)을, 그 경로에는 백슬래시 구분 기호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="59b20-122">WCF 终结点地址指定 msmq.formatname 方案，并为本地计算机使用 localhost。</span><span class="sxs-lookup"><span data-stu-id="59b20-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="59b20-123">각 MSMQ 형식 이름 주소 지정 지침의 큐 주소는 msmq.formatname 체계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="59b20-124">다음 샘플 코드에서와 같이 클라이언트 애플리케이션은 <xref:System.Messaging.MessageQueue.Send%2A> 메서드를 사용하여 지속적인 트랜잭션 메시지를 큐로 보내는 MSMQ 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

// Create the purchase order.
PurchaseOrder po = new PurchaseOrder();
po.CustomerId = "somecustomer.com";
po.PONumber = Guid.NewGuid().ToString();

PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
lineItem1.ProductId = "Blue Widget";
lineItem1.Quantity = 54;
lineItem1.UnitCost = 29.99F;

PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
lineItem2.ProductId = "Red Widget";
lineItem2.Quantity = 890;
lineItem2.UnitCost = 45.89F;

po.orderLineItems = new PurchaseOrderLineItem[2];
po.orderLineItems[0] = lineItem1;
po.orderLineItems[1] = lineItem2;

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="59b20-125">샘플을 실행하면 클라이언트 및 서비스 동작이 서비스 콘솔 창과 클라이언트 콘솔 창에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="59b20-126">서비스에서 클라이언트가 보내는 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="59b20-127">서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="59b20-128">큐를 사용하므로 클라이언트와 서비스가 동시에 실행 중일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="59b20-129">예를 들어 클라이언트를 실행하고 종료한 다음 서비스를 다시 시작해도 메시지를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="59b20-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="59b20-130">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="59b20-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="59b20-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="59b20-132">서비스가 처음 실행되는 경우 서비스에서는 큐가 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="59b20-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="59b20-133">큐가 없으면 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="59b20-134">서비스를 처음 실행하여 큐를 만들거나 MSMQ 큐 관리자를 통해 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="59b20-135">Windows 2008에서 큐를 만들려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="59b20-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="59b20-136">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="59b20-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="59b20-137">展开 "**功能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="59b20-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="59b20-138">右键单击 "**专用消息队列**"，然后选择 "**新建** **专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="59b20-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="59b20-139">选中 "**事务性**" 框。</span><span class="sxs-lookup"><span data-stu-id="59b20-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="59b20-140">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="59b20-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="59b20-141">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="59b20-142">若要在单计算机配置中运行示例，请按照[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="59b20-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="59b20-143">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="59b20-143">Run the sample across computers</span></span>

1. <span data-ttu-id="59b20-144">언어별 폴더의 \service\bin\ 폴더에서 서비스 컴퓨터로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="59b20-145">언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="59b20-146">Client.exe.config 파일에서 orderQueueName을 변경하여 "." 대신 서비스 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="59b20-147">서비스 컴퓨터의 명령 프롬프트에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="59b20-148">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59b20-149">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="59b20-150">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="59b20-150">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="59b20-151">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="59b20-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59b20-152">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59b20-152">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="59b20-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59b20-153">See also</span></span>

- [<span data-ttu-id="59b20-154">WCF의 큐</span><span class="sxs-lookup"><span data-stu-id="59b20-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="59b20-155">방법: WCF 엔드포인트 및 메시지 큐 애플리케이션과 메시지 교환</span><span class="sxs-lookup"><span data-stu-id="59b20-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="59b20-156">[消息队列](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="59b20-156">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
