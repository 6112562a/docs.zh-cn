---
title: 最佳做法：中介
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 8a95bd555e6c1acf896daa77e93d7c735d1f091c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663617"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="9f715-102">最佳做法：中介</span><span class="sxs-lookup"><span data-stu-id="9f715-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="9f715-103">当调用中介时务必谨慎，以便正确地处理故障，从而确保中介上的服务端通道正确关闭。</span><span class="sxs-lookup"><span data-stu-id="9f715-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="9f715-104">请考虑以下方案。</span><span class="sxs-lookup"><span data-stu-id="9f715-104">Consider the following scenario.</span></span> <span data-ttu-id="9f715-105">客户端调用中介，然后中介调用后端服务。</span><span class="sxs-lookup"><span data-stu-id="9f715-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="9f715-106">后端服务没有定义故障协定，因此，从该服务引发的任何故障都将被视为非类型化的故障。</span><span class="sxs-lookup"><span data-stu-id="9f715-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="9f715-107">后端服务，则会引发<xref:System.ApplicationException>和 WCF 正确地中止服务端通道。</span><span class="sxs-lookup"><span data-stu-id="9f715-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="9f715-108">然后，<xref:System.ApplicationException> 显示为一个要向中介引发的 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="9f715-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="9f715-109">中介重新引发 <xref:System.ApplicationException>。</span><span class="sxs-lookup"><span data-stu-id="9f715-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="9f715-110">WCF 将此解释为来自中介的非类型化故障，并将其转发到客户端。</span><span class="sxs-lookup"><span data-stu-id="9f715-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="9f715-111">收到故障后，中介和客户端会同时使其客户端通道出现故障。</span><span class="sxs-lookup"><span data-stu-id="9f715-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="9f715-112">但中介的客户端通道保持打开，因为 WCF 不知道故障是严重故障。</span><span class="sxs-lookup"><span data-stu-id="9f715-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="9f715-113">这种方案的最佳实践是检测来自服务的故障是否为严重故障，如果是，中介将使其服务端通道出现故障，如下面的代码段所示。</span><span class="sxs-lookup"><span data-stu-id="9f715-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f715-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="9f715-114">See also</span></span>
- [<span data-ttu-id="9f715-115">WCF 错误处理</span><span class="sxs-lookup"><span data-stu-id="9f715-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)
- [<span data-ttu-id="9f715-116">在协定和服务中指定并处理错误</span><span class="sxs-lookup"><span data-stu-id="9f715-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
