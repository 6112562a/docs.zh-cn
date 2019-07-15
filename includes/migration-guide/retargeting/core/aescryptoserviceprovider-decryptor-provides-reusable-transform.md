---
ms.openlocfilehash: 846a6bcd3c668e6ad505f745bcb830c3b9dce437
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859372"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>AesCryptoServiceProvider 解密器提供了可重用的转换

|   |   |
|---|---|
|详细信息|从面向 .NET Framework 4.6.2 的应用起，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密器提供了可重用的转换。 调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> 后，此转换将重新初始化并且可以重用。 对于面向旧版 .NET Framework 的应用，在调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> 后尝试通过调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> 重用解密器会引发 <xref:System.Security.Cryptography.CryptographicException> 或导致数据损坏。|
|建议|此更改的影响应该很小，因为这是预期的行为。对于依赖旧行为的应用程序，可通过将以下配置设置添加到应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分中，从而选择不用此更改：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>此外，对于面向旧版 .NET framework，但在 .NET Framework 4.6.2 及更高版本下运行的应用程序，可通过将以下配置设置添加到应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分，从而选择应用此更改：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.6.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|

