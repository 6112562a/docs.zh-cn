---
title: 인라인 코드를 사용한 IIS 호스팅
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 304da4fa7d2bb48899cdec864fb2dc1f9fdfb9ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746432"
---
# <a name="iis-hosting-using-inline-code"></a>인라인 코드를 사용한 IIS 호스팅

이 샘플에서는 IIS(인터넷 정보 서비스)에서 호스팅하는 서비스를 구현하는 방법을 보여 줍니다. 여기서 서비스 코드는 .svc 파일에 인라인으로 포함되어 있으며 필요할 때 컴파일됩니다. 또한 서비스 코드를 애플리케이션의 \App_Code 디렉터리에 있는 소스 코드 파일에서 직접 구현하거나 \bin에 배포된 어셈블리로 컴파일할 수 있습니다. 이 샘플에서는 이러한 기술은 보여 주지 않습니다.

> [!NOTE]
> 이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.

> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。 이 샘플은 다음 디렉터리에 있습니다.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

이 샘플에서는 요청-회신 통신 패턴을 정의하는 계약을 구현하는 일반적인 서비스를 보여 줍니다. 이 서비스는 IIS에서 호스팅되며 서비스 코드는 모두 Service.svc 파일에 포함되어 있습니다. 서비스는 호스트에서 활성화되며 서비스로 전송된 첫 번째 메시지에 의해 필요할 때 컴파일됩니다. 미리 컴파일할 필요는 없습니다. 서비스는 다음 코드에 정의된 대로 `ICalculator` 계약을 구현합니다.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

이 서비스 구현에서는 해당 결과를 계산하여 반환합니다.

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다. 클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>샘플을 설치, 빌드 및 실행하려면

1. 确保已对[Windows Communication Foundation 示例执行了一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)의 지침을 따릅니다.

3. 构建解决方案后，请运行 ServiceModelSamples 以在 IIS 7.0 中设置该应用程序。 现在，ServiceModelSamples 目录应显示为 IIS 7.0 应用程序。

4. 若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的说明进行操作。 有关如何创建可调用此服务的客户端应用程序的示例，请参阅[如何：创建客户端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。

## <a name="see-also"></a>另请参阅

- [AppFabric 宿主和持久性示例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
