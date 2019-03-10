---
title: 工作流事务
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: cb2a72bb24640d214170c52b8b3bf0a328d3f775
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714614"
---
# <a name="workflow-transactions"></a><span data-ttu-id="662e9-102">工作流事务</span><span class="sxs-lookup"><span data-stu-id="662e9-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="662e9-103">支持通过使用 <xref:System.Transactions> 活动确定事务处理工作单元的范围来参与 <xref:System.Activities.Statements.TransactionScope> 事务。</span><span class="sxs-lookup"><span data-stu-id="662e9-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="662e9-104">尽管必须显式完成 <xref:System.Transactions.TransactionScope?displayProperty=nameWithType>，但 <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> 活动在成功完成后将对事务隐式调用完成。</span><span class="sxs-lookup"><span data-stu-id="662e9-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="662e9-105"><xref:System.Activities.Statements.TransactionScope.Body%2A> 活动的 <xref:System.Activities.Statements.TransactionScope> 中包含的所有活动都会参与该事务。</span><span class="sxs-lookup"><span data-stu-id="662e9-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="662e9-106">通过使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动，WF 可以使事务流入某个工作流中。</span><span class="sxs-lookup"><span data-stu-id="662e9-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="662e9-107">与 <xref:System.Activities.Statements.TransactionScope> 活动一样，<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 中包含的所有活动都会参与该事务。</span><span class="sxs-lookup"><span data-stu-id="662e9-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="662e9-108">WF 确保依赖于 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> 的活动使用 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.ServiceModel.Activities.TransactedReceiveScope>。</span><span class="sxs-lookup"><span data-stu-id="662e9-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="662e9-109">如果系统提供的活动无法满足所有需求，可以使用 <xref:System.Activities.RuntimeTransactionHandle> 生成自定义活动，以便支持高级流控制和事务控制方案。</span><span class="sxs-lookup"><span data-stu-id="662e9-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="662e9-110">在以下示例中，工作流构造组成<xref:System.Activities.Statements.Sequence>活动，包含子活动包括<xref:System.Activities.Statements.TransactionScope>活动。</span><span class="sxs-lookup"><span data-stu-id="662e9-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="662e9-111">
  <xref:System.Activities.Statements.TransactionScope.Body%2A> 的 <xref:System.Activities.Statements.TransactionScope> 活动在 <xref:System.Activities.Statements.TransactionScope> 活动初始化的事务下执行。</span><span class="sxs-lookup"><span data-stu-id="662e9-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
<span data-ttu-id="662e9-112">有关详细信息，请参阅有关使用<xref:System.ServiceModel.Activities.TransactedReceiveScope>，请参阅[流动的事务和流出工作流服务](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="662e9-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662e9-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="662e9-113">See also</span></span>
- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
