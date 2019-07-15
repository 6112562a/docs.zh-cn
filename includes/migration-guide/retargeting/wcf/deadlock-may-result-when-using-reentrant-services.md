---
ms.openlocfilehash: 0aaa0ad0e0e3cbd23de287b3b79a8c209143544e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859320"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>使用可重入服务时可能导致死锁

|   |   |
|---|---|
|详细信息|死锁可能会导致一个可重入服务，该服务将服务的实例一次限制为一个执行线程。 代码中包含以下 <xref:System.ServiceModel.ServiceBehaviorAttribute> 的服务容易遇到此问题：<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|建议|要解决此问题，可执行以下操作：<ul><li>将服务的并发模式设置为 <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> 或 &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;。 例如:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>安装 .NET Framework 4.6.2 的最新更新，或升级到更高版本的 .NET Framework。 这将在 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中禁用 <xref:System.Threading.ExecutionContext> 的流。 此行为是可配置的；它相当于将以下应用设置添加到配置文件中：</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>对于 Rentrant 服务，<code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> 的值绝不能设置为 <code>false</code>。|
|范围|次要|
|版本|4.6.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

