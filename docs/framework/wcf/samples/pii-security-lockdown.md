---
title: PII 安全锁定
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144261"
---
# <a name="pii-security-lockdown"></a>PII 安全锁定
此示例演示如何通过以下方式控制 Windows 通信基础 （WCF） 服务的几个与安全相关的功能：  
  
- 加密服务配置文件中的敏感信息。  
  
- 锁定配置文件中的元素以使嵌套的服务子目录不能重写设置。  
  
- 控制跟踪和消息日志中的个人身份信息 (PII) 日志记录。  
  
> [!IMPORTANT]
> 您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目录不存在，请转到[Windows 通信基础 （WCF） 和 Windows 工作流基础 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下载[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基础 （WCF） 和示例。 此示例位于以下目录：  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>讨论区  
 这些功能中的每种功能都可以单独使用，也可以一起使用来控制服务安全的各个方面。 这不是保护 WCF 服务的明确指南。  
  
 .NET Framework 配置文件可以包含敏感信息，如用于连接到数据库的连接字符串。 在 Web 承载的共享方案中，可能需要对服务配置文件中的此信息进行加密，以避免他人无意中查看配置文件中包含的数据。 .NET Framework 2.0 和更高版本可以通过使用 Windows 数据保护应用程序编程接口 (DPAPI) 或 RSA 加密提供程序对配置文件的部分进行加密。 使用 DPAPI 或 RSA 的 aspnet_regiis.exe 可以对配置文件的选择部分进行加密。  
  
 在 Web 承载的方案中，可以使服务位于其他服务的子目录中。 用于确定配置值的默认语义允许嵌套目录中的配置文件重写父目录中的配置值。 在某些情况下，出于各种原因可能不希望这样做。 WCF 服务配置支持锁定配置值，以便在使用重写的配置值运行嵌套服务时生成异常。  
  
 此示例演示如何在跟踪和消息日志中控制已知个人身份信息 (PII) 日志记录，如用户名和密码。 默认情况下禁用已知 PII 的日志记录，但在特定情况下，PII 日志记录可能会对应用程序的调试大有帮助。 此示例基于[入门](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 此外，此示例还使用跟踪和消息日志记录。 有关详细信息，请参阅[跟踪和消息日志记录](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)示例。  
  
## <a name="encrypting-configuration-file-elements"></a>对配置文件元素进行加密  
 出于安全目的，在以 Web 为宿主的共享环境中，可能需要对包含敏感信息的特定配置元素（如数据库连接字符串）进行加密。 配置元素可以使用 .NET 框架文件夹中的 aspnet_regiis.exe 工具进行加密 例如，%WINDIR%\Microsoft.NET_Framework_v4.0.20728。  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>对示例的 Web.config 中的 appSettings 节中的值进行加密  
  
1. 使用"启动>运行"打开命令提示。 键入并`cmd`单击 **"确定**"。  
  
2. 通过发出下面的命令导航到当前的 .NET Framework 目录：`cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`。  
  
3. 通过发出下面的命令对 Web.config 文件夹中的 appSettings 配置设置进行加密：`aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`。  
  
 有关加密配置文件部分的详细信息，请参阅 ASP.NET 配置中的 DPAPI 操作操作（[构建安全ASP.NET应用程序：身份验证、授权和安全通信](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))）和 ASP.NET 配置中的 RSA 操作（[如何：使用 RSA ASP.NET 2.0 加密配置部分](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))）。  
  
## <a name="locking-configuration-file-elements"></a>锁定配置文件元素  
 在 Web 承载的方案中，可以使服务位于其他服务的子目录中。 在这些情况下，通过检查 Machine.config 中的值并依次与父目录中的任何 Web.config 文件合并，然后沿目录树向下移动，最后合并包含该服务的目录中的 Web.config 文件，来计算子目录中服务的配置值。 多数配置元素的默认行为都允许子目录中的配置文件重写父目录中设置的值。 在特定情况下，可能需要阻止子目录中的配置文件重写父目录配置中设置的值。  
  
 .NET Framework 提供了一种锁定配置文件元素的方式，当配置重写锁定的配置元素时会引发运行时异常。  
  
 通过在配置文件中指定节点的 `lockItem` 属性，可以锁定配置元素。例如，若要锁定配置文件中的 CalculatorServiceBehavior 节点以使嵌套的配置文件中的计算器服务无法更改该行为，可以使用下面的配置。  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>
          <serviceBehaviors>
             <behavior name="CalculatorServiceBehavior" lockItem="true">
               <serviceMetadata httpGetEnabled="True"/>
               <serviceDebug includeExceptionDetailInFaults="False" />
             </behavior>
          </serviceBehaviors>
       </behaviors>
    </system.serviceModel>  
</configuration>  
```  
  
 可以更具体地锁定配置元素。 可以指定元素的列表作为 `lockElements` 的值以锁定子元素集合中的一组元素。 可以指定属性的列表作为 `lockAttributes` 的值以锁定元素内的一组属性。 通过指定节点上的 `lockAllElementsExcept` 或 `lockAllAttributesExcept` 属性，可以锁定除指定列表外的整个元素集合或属性集合。  
  
## <a name="pii-logging-configuration"></a>PII 日志记录配置  
 PII 日志记录由两个开关控制：Machine.config 中可以让计算机管理员允许或拒绝 PII 日志记录的计算机范围的设置，和允许应用程序管理员针对 Web.config 或 App.config 文件中的每个源来切换 PII 日志记录的应用程序设置。  
  
 计算机范围的设置通过在 Machine.config `true` `false`中`machineSettings`的元素中的设置`enableLoggingKnownPii`或 控制。例如，以下允许应用程序打开 PII 的日志记录。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine.config 文件具有一个默认位置：%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG。  
  
 如果 Machine.config 中没有 `enableLoggingKnownPii` 属性，则不允许使用 PII 日志记录。  
  
 通过在 Web.config 或 App.config 文件中将源元素的 `logKnownPii` 属性设置为 `true` 或 `false`，可以对应用程序启用 PII 日志记录。 例如，下面的设置对消息日志记录和跟踪日志记录启用 PII 日志记录。  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>
                ...
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 如果未指定 `logKnownPii` 属性，则不记录 PII。  
  
 仅当 `enableLoggingKnownPii` 设置为 `true` 且 `logKnownPii` 设置为 `true` 时才会记录 PII。  
  
> [!NOTE]
> 除配置文件中列出的第一个属性外，System.Diagnostics 将忽略所有源上的所有属性。 向配置文件中的第二个源添加 `logKnownPii` 属性不起作用。  
  
> [!IMPORTANT]
> 要运行此示例，需要手动修改机器。修改 Machine.config 时应小心谨慎，因为不正确的值或语法可能会阻止所有 .NET 框架应用程序运行。  
  
 使用 DPAPI 和 RSA 也可以对配置文件元素进行加密。 有关更多信息，请参见下列链接：  
  
- [生成安全的 ASP.NET 应用程序：身份验证、授权和安全通信](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [如何：使用 RSA 加密 ASP.NET 2.0 中的配置节（可能为英文网页）](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1. 确保已为 Windows[通信基础示例执行一次性设置过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 编辑 Machine.config，将 `enableLoggingKnownPii` 属性设置为 `true`，需要时添加父节点。  
  
3. 若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
4. 要在单计算机或跨计算机配置中运行示例，请按照[运行 Windows 通信基础示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)说明操作。  
  
#### <a name="to-clean-up-the-sample"></a>清除示例  
  
1. 编辑 Machine.config，将 `enableLoggingKnownPii` 属性设置为 `false`。  
  
## <a name="see-also"></a>另请参阅

- [AppFabric 监视示例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
