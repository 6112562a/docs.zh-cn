---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236181"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="26950-101">WCF MsmqSecureHashAlgorithm 现在的默认值为 SHA256</span><span class="sxs-lookup"><span data-stu-id="26950-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="26950-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="26950-102">Details</span></span>|<span data-ttu-id="26950-103">自 .NET Framework 4.7.1 起，Msmq 消息 WCF 中的默认消息签名算法为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="26950-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="26950-104">在 .NET Framework 4.7 和更低版本中，默认消息签名算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="26950-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="26950-105">建议</span><span class="sxs-lookup"><span data-stu-id="26950-105">Suggestion</span></span>|<span data-ttu-id="26950-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，则可以通过将以下行添加到 app.config 文件的 <code>&lt;runtime&gt;</code> 部分选择退出更改：</span><span class="sxs-lookup"><span data-stu-id="26950-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="26950-107">范围</span><span class="sxs-lookup"><span data-stu-id="26950-107">Scope</span></span>|<span data-ttu-id="26950-108">次要</span><span class="sxs-lookup"><span data-stu-id="26950-108">Minor</span></span>|
|<span data-ttu-id="26950-109">版本</span><span class="sxs-lookup"><span data-stu-id="26950-109">Version</span></span>|<span data-ttu-id="26950-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="26950-110">4.7.1</span></span>|
|<span data-ttu-id="26950-111">类型</span><span class="sxs-lookup"><span data-stu-id="26950-111">Type</span></span>|<span data-ttu-id="26950-112">运行时</span><span class="sxs-lookup"><span data-stu-id="26950-112">Runtime</span></span>|
