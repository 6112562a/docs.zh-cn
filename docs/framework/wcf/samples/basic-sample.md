---
title: 기본 샘플
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 2ea5af0a1c05b5632632b2619c0ee4813696d2fc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738181"
---
# <a name="basic-sample"></a>기본 샘플

이 샘플에서는 서비스를 검색 가능하게 만드는 방법과 검색 가능한 서비스를 검색하고 호출하는 방법을 보여 줍니다. 이 샘플은 서비스와 클라이언트에 해당하는 두 개의 프로젝트로 구성되어 있습니다.

> [!NOTE]
> 이 샘플은 코드에서 검색을 구현합니다.  有关在配置中实现发现的示例，请参阅[配置](../../../../docs/framework/wcf/samples/configuration-sample.md)。

## <a name="service"></a>서비스

간단한 계산기 서비스 구현입니다. 검색 관련 코드는 `Main`에 있으며, 여기에서 다음 코드와 같이 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>가 서비스 호스트에 추가되고 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>가 추가됩니다.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a>Client

클라이언트에서는 <xref:System.ServiceModel.Discovery.DynamicEndpoint>를 사용하여 서비스를 찾습니다. 표준 엔드포인트인 <xref:System.ServiceModel.Discovery.DynamicEndpoint>는 클라이언트가 열릴 때 서비스의 엔드포인트를 확인합니다. 이 경우 <xref:System.ServiceModel.Discovery.DynamicEndpoint>는 서비스 계약에 따라 서비스를 찾습니다. <xref:System.ServiceModel.Discovery.DynamicEndpoint>는 기본적으로 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>에 대한 검색을 수행합니다. 서비스 엔드포인트를 찾은 후 클라이언트는 지정된 바인딩을 통해 해당 서비스에 연결합니다.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

클라이언트는 `InvokeCalculatorService` 클래스를 사용하여 서비스를 검색하는 <xref:System.ServiceModel.Discovery.DiscoveryClient>라는 메서드를 정의합니다. <xref:System.ServiceModel.Discovery.DynamicEndpoint>는 <xref:System.ServiceModel.Description.ServiceEndpoint>에서 상속하므로 `InvokeCalculatorService` 메서드에 전달될 수 있습니다. 그런 다음 예제에서는 <xref:System.ServiceModel.Discovery.DynamicEndpoint>를 사용하여 `CalculatorServiceClient`의 인스턴스를 만들고 계산기 서비스의 다양한 작업을 호출합니다.

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a>이 샘플을 사용하려면

1. 이 샘플에서는 HTTP 엔드포인트를 사용하며 이 샘플을 실행하려면 적절한 URL ACL을 추가해야 합니다. 有关详细信息，请参阅[配置 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。 높은 권한으로 다음 명령을 실행하면 적절한 ACL이 추가됩니다. 명령이 지정한 대로 작동하지 않는 경우 다음 인수의 도메인과 사용자 이름을 대체할 수 있습니다. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. 使用 Visual Studio 2012，打开基本 .sln 并生成示例。

3. service.exe 애플리케이션을 실행합니다.

4. 서비스가 시작된 후 client.exe를 실행합니다.

5. 클라이언트에서 주소를 모르고도 서비스를 찾을 수 있는지 확인합니다.

> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。 이 샘플은 다음 디렉터리에 있습니다.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
