---
title: 从应用程序域中检索安装信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053104"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="3f381-102">从应用程序域中检索安装信息</span><span class="sxs-lookup"><span data-stu-id="3f381-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="3f381-103">应用程序域的每个实例由属性和 <xref:System.AppDomainSetup> 信息组成。</span><span class="sxs-lookup"><span data-stu-id="3f381-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="3f381-104">可使用 <xref:System.AppDomain?displayProperty=nameWithType> 类从应用程序域中检索安装信息。</span><span class="sxs-lookup"><span data-stu-id="3f381-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3f381-105">此类提供多个成员，可用于检索应用程序域的相关配置信息。</span><span class="sxs-lookup"><span data-stu-id="3f381-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="3f381-106">还可以查询应用程序域的 AppDomainSetup 对象，获取创建域时传递到该域的安装信息。</span><span class="sxs-lookup"><span data-stu-id="3f381-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="3f381-107">下面的示例创建新的应用程序域，然后将几个成员值打印到控制台。</span><span class="sxs-lookup"><span data-stu-id="3f381-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="3f381-108">下面的示例设置并检索某一应用程序域的安装信息。</span><span class="sxs-lookup"><span data-stu-id="3f381-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="3f381-109">请注意，`AppDomain.SetupInformation.ApplicationBase` 获取配置信息。</span><span class="sxs-lookup"><span data-stu-id="3f381-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3f381-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f381-110">See also</span></span>

- [<span data-ttu-id="3f381-111">对应用程序域进行编程</span><span class="sxs-lookup"><span data-stu-id="3f381-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="3f381-112">使用应用程序域</span><span class="sxs-lookup"><span data-stu-id="3f381-112">Using Application Domains</span></span>](use.md)
