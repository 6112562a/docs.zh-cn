---
title: 程序工作流
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956106"
---
# <a name="procedural-workflows"></a>程序工作流
程序工作流使用的流控制方法与程序语言中使用的流控制方法类似。 这些构造包括 `While` 和 `If`。 使用 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Sequence> 等其他流控制活动，可以随意组合这些工作流。  
  
## <a name="controlling-execution-flow"></a>控制执行流  
 工作流活动库包含的活动可用于对程序语言中使用的大多数流控制方法进行建模， 这些问题包括：  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 若要使用流控制活动, 请将**活动**工具箱中的这些活动拖放到设计器窗口内的复合活动。  
  
> [!NOTE]
> 如果使用 Windows Server AppFabric 的承载功能在 Web 场上托管工作流, 则 AppFabric 将在不同的 AppFabric 服务器之间移动实例。 这就需要资源在所有节点之间可以共享。  默认 NET 4 工作流活动不包含访问本地资源的任何操作。 由于 AppFabric 没有提供将工作流标记为可移动的机制，所以开发人员不能在移动工作流时创建自定义活动。  
  
## <a name="see-also"></a>请参阅

- [流程图工作流](flowchart-workflows.md)
