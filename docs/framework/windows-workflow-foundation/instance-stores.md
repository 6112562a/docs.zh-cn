---
title: 实例存储区
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 352ffad56c77d0bd16f7e3b9aa1d82090f3a29b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791165"
---
# <a name="instance-stores"></a>实例存储区
实例存储区是实例的逻辑容器。 它是实例数据和元数据的存储位置。 实例存储区不表示专用物理存储区。 实例存储区可以包含 SQL Server 数据库中的持久性信息或内存中的非持久状态信息。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]附带的 SQL 工作流实例存储是实例存储区的具体实现，它允许工作流在 SQL Server 2005 或 SQL Server 2008 数据库中持久保存实例数据和元数据。 此外，Windows Server App Fabric 还提供了实例存储区的具体实现。 有关详细信息，请参阅[Windows Server App Fabric 实例存储区、 查询和管理提供程序](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409)。  
  
 持久性 API 是宿主与实例存储区之间的接口，允许宿主向实例存储区发送命令请求（例如，<xref:System.Activities.DurableInstancing.LoadWorkflowCommand> 和 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>）。 该 API 的具体实施被称为持久性提供程序。 持久性提供程序收到宿主的请求，并修改实例存储区。  
  
 宿主与实例存储区是可插入的，这样一个宿主可用于多个实例存储区，一个实例存储区也可用于多个宿主。 虽然实例存储区和宿主可在独立的生命周期中演变，但通常会针对特定宿主的使用模式来优化实例存储区。 例如， **WorkflowServiceHost**并**SqlWorkflowInstanceStore**旨在很好地协同工作。 您可以创建自己的实例存储区，以保留数据和元数据的工作流服务实例，并使用与该实例存储区**WorkflowServiceHost**。 例如，可创建 OracleWorkflowInstanceStore，以使工作流能够将信息持久保存到 Oracle 数据库中，而不是将它们保存到 SQL Server 数据库中。  
  
 通常会为宿主扩展附加功能，从而修改持久保存的对象。 例如，某个实例持久性系统可能会有工作流宿主，支持"挂起"操作和 SQL 实例存储区的扩展。  工作流宿主可能发送标准命令，如“保存”或“加载”，以便保存实例存储区中的工作流或从实例存储区加载工作流，或将工作流保存到实例存储区中。 挂起扩展可能将附加语义添加到命令中来保存和加载工作流实例，使挂起的工作流实例无法加载。 SQL 实例存储区的持久性提供程序了解保存和加载工作流实例的命令，并通过调用可更改 SQL Server 数据库中的持久性对象表的适当存储过程来执行命令。  
  
 在实例存储区中，宿主充当实例所有者。 宿主可以同时充当多个实例所有者，拥有多个实例存储区。 宿主为与实例相关的实例键提供 GUID。 实例键是识别实例的唯一别名。 持久性系统在执行宿主请求的命令时将创建、更新和删除实例所有者信息。  
  
 以下列表包含了涉及宿主与实例存储区交互的重要步骤：  
  
1. 获取**InstanceStore**从持久性提供程序。  

2. 通过调用获取实例的句柄<xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A>方法**InstanceStore**。  
  
3. 通过调用调用针对实例句柄的命令<xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A>方法**InstanceStore**。  
  
4. 检查<xref:System.Runtime.DurableInstancing.InstanceView>返回的**InstanceStore.Execute**来确定命令的结果。
