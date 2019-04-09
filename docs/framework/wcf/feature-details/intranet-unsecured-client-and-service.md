---
title: 不安全的 Intranet 客户端和服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 540c0fe5c4d06ea341b9cc8be9755cc67fe9bbc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085176"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="06c4d-102">不安全的 Intranet 客户端和服务</span><span class="sxs-lookup"><span data-stu-id="06c4d-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="06c4d-103">下图描绘了开发到 WCF 应用程序安全的专用网络上提供信息的简单 Windows Communication Foundation (WCF) 服务。</span><span class="sxs-lookup"><span data-stu-id="06c4d-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="06c4d-104">不需要安全，因为数据重要性较低、 网络应为本质上是安全的或者在通过以下 WCF 基础结构的层来提供安全性。</span><span class="sxs-lookup"><span data-stu-id="06c4d-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![不安全的 intranet 客户端和服务方案。](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="06c4d-106">特征</span><span class="sxs-lookup"><span data-stu-id="06c4d-106">Characteristic</span></span>|<span data-ttu-id="06c4d-107">描述</span><span class="sxs-lookup"><span data-stu-id="06c4d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="06c4d-108">安全模式</span><span class="sxs-lookup"><span data-stu-id="06c4d-108">Security Mode</span></span>|<span data-ttu-id="06c4d-109">None</span><span class="sxs-lookup"><span data-stu-id="06c4d-109">None</span></span>|  
|<span data-ttu-id="06c4d-110">传输</span><span class="sxs-lookup"><span data-stu-id="06c4d-110">Transport</span></span>|<span data-ttu-id="06c4d-111">TCP</span><span class="sxs-lookup"><span data-stu-id="06c4d-111">TCP</span></span>|  
|<span data-ttu-id="06c4d-112">绑定</span><span class="sxs-lookup"><span data-stu-id="06c4d-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="06c4d-113">互操作性</span><span class="sxs-lookup"><span data-stu-id="06c4d-113">Interoperability</span></span>|<span data-ttu-id="06c4d-114">WCF 仅</span><span class="sxs-lookup"><span data-stu-id="06c4d-114">WCF only</span></span>|  
|<span data-ttu-id="06c4d-115">身份验证</span><span class="sxs-lookup"><span data-stu-id="06c4d-115">Authentication</span></span>|<span data-ttu-id="06c4d-116">None</span><span class="sxs-lookup"><span data-stu-id="06c4d-116">None</span></span>|  
|<span data-ttu-id="06c4d-117">完整性</span><span class="sxs-lookup"><span data-stu-id="06c4d-117">Integrity</span></span>|<span data-ttu-id="06c4d-118">None</span><span class="sxs-lookup"><span data-stu-id="06c4d-118">None</span></span>|  
|<span data-ttu-id="06c4d-119">保密性</span><span class="sxs-lookup"><span data-stu-id="06c4d-119">Confidentiality</span></span>|<span data-ttu-id="06c4d-120">None</span><span class="sxs-lookup"><span data-stu-id="06c4d-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="06c4d-121">服务</span><span class="sxs-lookup"><span data-stu-id="06c4d-121">Service</span></span>  
 <span data-ttu-id="06c4d-122">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="06c4d-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="06c4d-123">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="06c4d-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="06c4d-124">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="06c4d-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="06c4d-125">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="06c4d-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="06c4d-126">代码</span><span class="sxs-lookup"><span data-stu-id="06c4d-126">Code</span></span>  
 <span data-ttu-id="06c4d-127">下面的代码演示如何创建不安全的终结点：</span><span class="sxs-lookup"><span data-stu-id="06c4d-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="06c4d-128">配置</span><span class="sxs-lookup"><span data-stu-id="06c4d-128">Configuration</span></span>  
 <span data-ttu-id="06c4d-129">下面的代码使用配置设置相同的终结点：</span><span class="sxs-lookup"><span data-stu-id="06c4d-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="06c4d-130">客户端</span><span class="sxs-lookup"><span data-stu-id="06c4d-130">Client</span></span>  
 <span data-ttu-id="06c4d-131">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="06c4d-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="06c4d-132">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="06c4d-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="06c4d-133">使用代码（和客户端代码）创建独立客户端。</span><span class="sxs-lookup"><span data-stu-id="06c4d-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="06c4d-134">创建不定义任何终结点地址的客户端。</span><span class="sxs-lookup"><span data-stu-id="06c4d-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="06c4d-135">而使用将配置名称作为自变量的客户端构造函数。</span><span class="sxs-lookup"><span data-stu-id="06c4d-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="06c4d-136">例如：</span><span class="sxs-lookup"><span data-stu-id="06c4d-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="06c4d-137">代码</span><span class="sxs-lookup"><span data-stu-id="06c4d-137">Code</span></span>  
 <span data-ttu-id="06c4d-138">下面的代码演示一个基本的 WCF 客户端访问不安全终结点使用 TCP 协议。</span><span class="sxs-lookup"><span data-stu-id="06c4d-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="06c4d-139">配置</span><span class="sxs-lookup"><span data-stu-id="06c4d-139">Configuration</span></span>  
 <span data-ttu-id="06c4d-140">下面的配置代码应用于客户端：</span><span class="sxs-lookup"><span data-stu-id="06c4d-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06c4d-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="06c4d-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="06c4d-142">安全性概述</span><span class="sxs-lookup"><span data-stu-id="06c4d-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="06c4d-143">Windows Server App Fabric 的安全模型</span><span class="sxs-lookup"><span data-stu-id="06c4d-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
