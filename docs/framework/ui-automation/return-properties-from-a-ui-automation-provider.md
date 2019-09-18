---
title: 从 UI 自动化提供程序返回属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 5d073af121eae04a973667739c68a90d6dae9f2d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042736"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="1122d-102">从 UI 自动化提供程序返回属性</span><span class="sxs-lookup"><span data-stu-id="1122d-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="1122d-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="1122d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1122d-104">有关的最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 请[参阅 Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="1122d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1122d-105">本主题包含显示 UI 自动化提供程序如何才能将元素的属性返回到客户端应用程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="1122d-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="1122d-106">对于不显式支持的任何属性，则提供程序必须返回 `null` （Visual Basic 中为`Nothing` ）。</span><span class="sxs-lookup"><span data-stu-id="1122d-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="1122d-107">这样可确保 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 试图获取来自另一个源（如宿主窗口提供程序）的属性。</span><span class="sxs-lookup"><span data-stu-id="1122d-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1122d-108">示例</span><span class="sxs-lookup"><span data-stu-id="1122d-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="1122d-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="1122d-109">See also</span></span>

- [<span data-ttu-id="1122d-110">UI 自动化提供程序概述</span><span class="sxs-lookup"><span data-stu-id="1122d-110">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="1122d-111">服务器端 UI 自动化提供程序实现</span><span class="sxs-lookup"><span data-stu-id="1122d-111">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
