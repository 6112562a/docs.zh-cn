---
title: WAS Activation 아키텍처
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 01c30db1182ece6dd968b69cc4efcaa2d9fabd79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737513"
---
# <a name="was-activation-architecture"></a>WAS Activation 아키텍처
이 항목에서는 Windows Process Activation Service(WAS라고도 함)의 구성 요소를 항목별로 정리하고 설명합니다.  
  
## <a name="activation-components"></a>활성화 구성 요소  
 WAS는 여러 가지 아키텍처 구성 요소로 구성됩니다.  
  
- 수신기 어댑터. 특정 네트워크 프로토콜에서 메시지를 받고, 들어오는 메시지를 올바른 작업자 프로세스로 라우트하기 위해 WAS와 통신하는 Windows 서비스입니다.  
  
- WAS. 작업자 프로세스 만들기 및 수명을 관리하는 Windows 서비스입니다.  
  
- 제네릭 작업자 프로세스 실행 파일(w3wp.exe).  
  
- 애플리케이션 관리자. 작업자 프로세스 내에서 애플리케이션을 호스팅하는 애플리케이션 도메인 만들기 및 수명을 관리합니다.  
  
- 프로토콜 처리기. 작업자 프로세스에서 실행되고 작업자 프로세스와 개별 수신기 어댑터 간 통신을 관리하는 프로토콜 관련 구성 요소입니다. 프로토콜 처리기 형식에는 프로세스 프로토콜 처리기와 AppDomain 프로토콜 처리기가 있습니다.  
  
 WAS가 작업자 프로세스 인스턴스를 활성화하면 작업자 프로세스에 필요한 프로세스 프로토콜 처리기를 로드하고, 애플리케이션 관리자를 사용하여 애플리케이션을 호스트할 애플리케이션 도메인을 만듭니다. 애플리케이션 도메인은 애플리케이션에서 사용하는 네트워크 프로토콜에 필요한 AppDomain 프로토콜 처리기와 애플리케이션의 코드를 로드합니다.  
  
 ![显示 WAS 体系结构的屏幕截图。](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>수신기 어댑터  
 수신기 어댑터는 수신 대기하는 네트워크 프로토콜을 사용하여 메시지를 받는 데 사용되는 네트워크 통신 논리를 구현하는 개별 Windows 서비스입니다. 下表列出了用于 Windows Communication Foundation （WCF）协议的侦听器适配器。  
  
|수신기 어댑터 서비스 이름|프로토콜|참고|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|提供 IIS 7.0 和 WCF HTTP 激活的通用组件。|  
|NetTcpActivator|net.tcp|NetTcpPortSharing 서비스에 따라 다릅니다.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|用于基于 WCF 的消息队列应用程序。|  
|NetMsmqActivator|msmq.formatname|이전 버전의 기존 메시지 큐 애플리케이션과의 호환성을 제공합니다.|  
  
 특정 프로토콜의 수신기 어댑터는 다음 XML 예제에서처럼 설치하는 동안 applicationHost.config 파일에 등록됩니다.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>프로토콜 처리기  
 특정 프로토콜에 대한 프로세스 및 AppDomain 프로토콜 처리기는 시스템 수준의 Web.config 파일에 등록됩니다.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>另请参阅

- [WCF와 함께 사용하도록 WAS 구성](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Windows Server App Fabric 호스팅 기능](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
