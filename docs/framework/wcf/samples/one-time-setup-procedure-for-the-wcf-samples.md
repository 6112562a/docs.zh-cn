---
title: Windows Communication Foundation 샘플의 일회 설치 절차
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: b75dd523d4c88eae70f8d21ac8b3c9f72ae055ed
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744785"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation 샘플의 일회 설치 절차

大多数 Windows Communication Foundation （WCF）示例承载于 Internet Information Services （IIS）中并从公共虚拟目录运行。 此一次性安装过程在磁盘上创建一个文件夹;它还向 IIS 添加一个名为**ServiceModelSamples**的虚拟目录。

**ServiceModelSamples**虚拟目录用于生成和运行使用 IIS 承载的服务的所有示例。 이 디렉터리는 샘플을 실행하는 데 필요한 유일한 가상 디렉터리입니다. 샘플을 빌드하면 이 가상 디렉터리에서 이전에 배포된 서비스가 대체되고 가장 최근에 빌드된 샘플만 배포되어 이 가상 디렉터리에서 사용할 수 있게 됩니다.

> [!NOTE]
> 모든 명령을 로컬 관리자 계정으로 실행해야 합니다. 如果你使用的是 Windows 7、Windows Vista 或 Windows Server 2008 R2，则还必须使用提升的权限运行命令提示符。 为此，请右键单击 "命令提示符" 图标，然后单击 "以**管理员身份运行**"。 이 항목의 모든 명령은 경로 설정이 적절한 명령 프롬프트에서 실행해야 합니다.  이를 위한 가장 쉬운 방법은 Visual Studio 명령 프롬프트를 사용하는 것입니다. 若要打开此提示，请单击 "**开始**"，选择 "**所有程序**"，向下滚动到 " **visual studio 2010**"，选择**Visual Studio Tools**，右键单击 " **visual studio 命令提示符（2010）** "，然后单击 "以**管理员身份运行**"。 Visual Studio Express Edition 중 하나가 설치되어 있어 이 명령 프롬프트를 사용할 수 없는 경우에는 시스템 경로에 "C:\Windows\Microsoft.Net\Framework\v4.0"을 추가해야 합니다.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF 샘플의 일회 설치 절차

1. 确保已设置 ASP.NET。 有关如何设置 ASP.NET 的详细信息，请参阅[Internet 信息服务托管说明](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)。

2. 确保安装 .NET Framework 4。 在以下目录中搜索 v2.0 （或更高版本）： **\Windows\Microsoft.NET\Framework**

3. 请确保已安装 Visual Studio 2012 或更高版本，或者你的操作系统为 Windows Server 2008 SP2 或更高版本。

4. 다음 명령을 실행합니다. 有关这些命令必须运行的详细信息，请参阅[IIS 托管服务失败](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))。

    > [!WARNING]
    > IIS가 다시 설치된 경우 다음 명령을 다시 실행해야 합니다.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > 运行命令 `aspnet_regiis –i –enable` 会使默认应用池使用 .NET Framework 4 运行，这可能会为同一台计算机上的其他应用程序产生不兼容问题。

5. 按照[防火墙说明](../../../../docs/framework/wcf/samples/firewall-instructions.md)启用示例使用的端口。

6. 检查以下默认目录： \<安装驱动器 >： **\ WF_WCF_Samples**。 샘플이 이전에 설치된 경우 이 디렉터리가 기본 디렉터리입니다.

7. 如果未安装这些示例，请从的示例下载位置安装这些示例[C#](https://go.microsoft.com/fwlink/?LinkId=190939)。

8. 安装示例后，请参阅： \<安装驱动器 >： **\ WF_WCF_Samples \wcf\setup\\**

9. 运行**setupvroot.bat**批处理文件。 다음 단계가 수행됩니다.

    - IIS에 ServiceModelSamples라는 가상 디렉터리가 만들어집니다.

    - %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples and %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin이라는 새 디스크 디렉터리가 만들어집니다.

    如果想要手动设置这些目录，请参阅[虚拟目录设置说明](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md)。 이 단계에서 수행한 모든 변경 작업을 되돌리려면 샘플 사용을 마친 후 cleanupvroot.bat를 실행합니다.

    > [!NOTE]
    > cleanupvroot.bat가 실행되지 않은 경우 이 절차는 한 컴퓨터에서 한 번만 수행해야 합니다.

10. 샘플을 빌드 중인 계정과 Network Service 사용자에 %SystemDrive%\inetpub\wwwroot에 대한 수정 권한을 부여해야 합니다. 빌드하는 동안 일부 웹 호스팅 샘플은 컴파일된 이진 파일을 앞에서 설명한 위치에 복사하려고 시도하므로 적절한 사용 권한이 설정되지 않은 경우 빌드가 중지됩니다. 或者，你可以将这些权限保留原样，并以管理员身份运行 SDK 命令提示或 Visual Studio 命令提示符（2012），或在 Visual Studio 2012 中生成示例，同时以管理员身份运行。

    > [!NOTE]
    > 이 단계를 완료하지 않으면 IIS에서 호스팅되는 모든 샘플이 빌드 중에 실패합니다. 사용 권한을 올바르게 설정했는지 확인하거나 SDK 명령 프롬프트와 Visual Studio 명령 프롬프트(2012)를 관리자 권한으로 실행하십시오.

11. 컴퓨터에 C:\logs 디렉터리를 만듭니다. 일부 샘플에 이 디렉터리가 필요할 수 있습니다. 적절한 계정에 이 폴더에 대한 쓰기 권한을 부여해야 합니다. 对于 Windows 7、Windows Vista 和 Windows Server 2008 R2，此帐户为**Network Service**。 对于 Windows Server 2008，该帐户为 NT Authority\Network Service。 对于 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 Windows Server 2003，帐户为 ASPNET。

12. Setupcerttool.bat 파일을 실행합니다. 此文件位于 \<InstallPath > \ WF_WCF_Samples \WCF\Setup\ 文件夹中。  이 스크립트는 다음 작업을 수행합니다.

    - FindPrivateKey 도구를 빌드합니다.

    - %ProgramFiles%\ServiceModelSampleTools라는 디렉터리를 만듭니다.

    - 이 디렉터리에 새 FindPrivateKey 도구를 복사합니다.

    이 도구는 인증서를 사용하고 IIS에서 호스팅되는 샘플에 필요합니다.

    > [!NOTE]
    > 보안을 위해 샘플 사용이 끝나면 Cleanupvroot.bat라는 배치 파일을 실행하여 설치 단계에서 부여된 가상 디렉터리 정의와 사용 권한을 제거해야 합니다.

13. IIS에서 호스팅되지 않고 자체 호스팅되는 샘플의 경우 수신 대기를 위해 컴퓨터에서 HTTP 주소를 등록할 수 있는 권한이 필요합니다. HTTP 네임스페이스 예약을 위한 사용 권한은 샘플을 실행하는 데 사용되는 사용자 계정에서 제공됩니다. 기본적으로 관리자 계정에는 모든 HTTP 주소를 등록할 수 있는 사용 권한이 있습니다. 관리자 이외의 계정에는 샘플에 사용되는 HTTP 네임스페이스에 대한 권한을 부여해야 합니다. 네임스페이스 예약을 구성하는 방법에 대한 자세한 내용은 [HTTP 및 HTTPS 구성](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)을 참조하세요.

14. 일부 샘플에는 메시지 큐가 필요합니다. 有关安装说明，请参阅[安装消息队列（MSMQ）](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) 。

    > [!NOTE]
    > 메시지 큐가 필요한 샘플을 실행하려면 먼저 MSMQ 서비스를 시작해야 합니다.

15. 일부 샘플에는 인증서가 필요합니다. 请参阅[Internet Information Services （IIS）服务器证书安装说明](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。
