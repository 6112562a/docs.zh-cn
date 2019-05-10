---
title: 访问资源时的安全信任级别
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 847467b964e86f6d13be6ba103162512270fa684
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596761"
---
# <a name="security-trust-levels-in-accessing-resources"></a>访问资源时的安全信任级别
本主题讨论如何限制对 <xref:System.Transactions> 所公开的资源类型的访问。  
  
 <xref:System.Transactions> 主要有三种信任级别。 定义这些信任级别时根据的是 <xref:System.Transactions> 所公开的资源类型以及访问这些资源所需的信任级别。 <xref:System.Transactions> 可访问的资源有系统内存、共享进程范围的资源以及系统范围的资源。 这些级别包括：  
  
- **AllowPartiallyTrustedCallers** (APTCA) 在单个应用程序域中使用事务的应用程序。  
  
- **DistributedTransactionPermission** (DTP) 使用分布式的事务的应用程序。  
  
- 完全信任，适用于持久资源、配置管理应用程序和旧版互操作应用程序。  
  
> [!NOTE]
>  不能在模拟上下文中调用任何登记接口。  
  
## <a name="trust-levels"></a>信任级别  
  
### <a name="aptca-partial-trust"></a>APTCA（部分信任）  
 <xref:System.Transactions>程序集可以由部分受信任代码调用，因为它已标记有**AllowPartiallyTrustedCallers**特性 (APTCA)。 此属性实质上是移除了的隐式<xref:System.Security.Permissions.SecurityAction.LinkDemand>有关**FullTrust**权限集，它是否则自动放置在每种类型的每个可公开访问方法。 但是，某些类型和成员还是需要更强的权限。  
  
 APTCA 特性使应用程序可以在单个应用程序域中以部分信任级别使用事务。 这会启用未升级的事务和可用于错误处理的可变登记。 事务处理哈希表和使用它的应用程序就属于这种情况。 可在单个事务下的哈希表中添加和移除数据。 如果以后回滚该事务，则对该事务下哈希表的所有更改都可撤消。  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 当 <xref:System.Transactions> 事务升级为由 MSDTC 进行管理时，<xref:System.Transactions> 会要求提供 <xref:System.Transactions.DistributedTransactionPermission> (DTP) 以创建分布式事务。 这意味着需要向用于使事务升级（例如，通过序列化或其他持久登记）的代码授予 DTP。 最初创建了 <xref:System.Transactions> 事务的代码无需拥有此权限。  
  
### <a name="fulltrust-link-demands"></a>FullTrust 链接要求  
 此权限级别旨在限制要写入持久资源的应用程序。 在出现故障时，应用程序需要能够使用事务管理器进行恢复，以确定事务的最终结果，从而可以更新永久数据。 这种应用程序称为持久源管理器。 SQL 就是这种应用程序的典型示例。  
  
 若要启用恢复功能，这种应用程序应具备永久使用系统资源的能力。 这是因为可恢复的事务管理器必须记住已提交的事务，直到它可确认参与事务的所有持久资源管理器都已接收到结果。 因此，这种应用程序要求完全信任权限，因此它只有在已被授予该信任级别的情况下才能运行。  
  
 有关持久登记和恢复的详细信息，请参阅[登记为参与者在事务中的资源](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)并[Performing Recovery](../../../../docs/framework/data/transactions/performing-recovery.md)主题。  
  
 此外，使用 COM+ 执行旧版互操作的应用程序也需要具有完全信任级别。  
  
 以下是类型的列表，原因是它们修饰的成员部分不是可被调用的受信任的代码**FullTrust**声明性安全属性：  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 只需拥有直接调用方**FullTrust**权限设置为使用上述类型或方法。
